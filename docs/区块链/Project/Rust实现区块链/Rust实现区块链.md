## [Basic Prototype](https://jeiwan.net/posts/building-blockchain-in-go-part-1/)

### 区块Block

一个简化版的区块链，区块仅包含了部分关键信息，它的数据结构如下：

```rust
pub struct Block {
    pub timestamp: u64,
    pub data: Vec<u8>,
    pub prev_block_hash: Vec<u8>,
    pub hash: Vec<u8>,
}
```

|      字段       | 解释                               |
| :-------------: | :--------------------------------- |
|   `Timestamp`   | 当前时间戳，也就是区块创建的时间   |
| `PrevBlockHash` | 前一个块的哈希，即父哈希           |
|     `Hash`      | 当前块的哈希                       |
|     `Data`      | 区块存储的实际有效信息，也就是交易 |

这里的 `Timestamp`，`PrevBlockHash`, `Hash`，在比特币技术规范中属于区块头（block header），区块头是一个单独的数据结构。完整的 [比特币的区块头（block header）结构](https://en.bitcoin.it/wiki/Block_hashing_algorithm) ，比特币的 golang 实现 btcd 的 [BlockHeader](https://github.com/btcsuite/btcd/blob/01f26a142be8a55b06db04da906163cd9c31be2b/wire/blockheader.go#L20-L41) 定义



而我们的 `Data`, 在比特币中对应的是**交易，是另一个单独的数据结构**。为了简便起见，目前将这两个数据结构放在了一起。在真正的比特币中，[区块](https://en.bitcoin.it/wiki/Block#Block_structure) 的数据结构



在我们的简化版区块中，还有一个 `Hash` 字段，那么，要如何计算哈希呢？

仅取了 `Block` 结构的部分字段（`Timestamp`, `Data` 和 `PrevBlockHash`），并将它们相互拼接起来，然后在拼接后的结果上计算一个 SHA-256，然后就得到了哈希.

```
Hash = SHA256(PrevBlockHash + Timestamp + Data)
```

在 `SetHash` 方法中完成这些操作：

```rust
    /// Set hash function
    /// Hash = SHA256(PrevBlockHash + Timestamp + Data)
    pub fn set_hash(&mut self) {
        let timestamp = self.timestamp.to_string().into_bytes();
        let headers = [self.prev_block_hash.clone(), self.data.clone(), timestamp].concat();
        let mut hasher = Sha256::new();
        hasher.update(&headers);
        let hash = hasher.finalize();
        self.hash = hash.to_vec();
    }
```

实现一个用于简化创建区块的函数 `NewBlock`：

```rust
    /// Create a new block
    pub fn new_block(data: &str, prev_block_hash: Vec<u8>) -> Block {
        // get timestamp
        let timestamp = SystemTime::now()
            .duration_since(UNIX_EPOCH)
            .unwrap()
            .as_secs();
        let mut block = Block::new(
            timestamp,
            data.to_string().into_bytes(),
            prev_block_hash,
            [].to_vec(),
        );
        // update hash
        block.set_hash();
        block
    }
```



### 区块链

有了区块，下面让我们来实现区块**链**。

区块按照插入的顺序进行存储，每个块都与前一个块相连。这样的结构，能够让我们快速地获取链上的最新块，并且高效地通过哈希来检索一个块。

用Rust的Vec<>来实现

```rust
pub struct BlockChain {
    pub blocks: Vec<Block>,
}

```

这就是我们的第一个区块链, 就是一个 `Block` 数组。

现在，让我们能够给它添加一个区块：

```rust
    /// Build blockchain
    pub fn new_blockchain() -> BlockChain {
        let genesis_block = BlockChain::new_genesis_block();
        BlockChain {
            blocks: [genesis_block].to_vec(),
        }
    }
```



为了加入一个新的块，我们必须要有一个已有的块，但是，初始状态下，我们的链是空的，一个块都没有！所以，在任何一个区块链中，都必须至少有一个块。这个块，也就是链中的第一个块，通常叫做创世块（**genesis block**）. 让我们实现一个方法来创建创世块：

```rust
    /// Create genesis block(The first block in blockchain)
    pub fn new_genesis_block() -> Block {
        Block::new_block("Genesis Block", [].to_vec())
    }
```

现在，我们可以实现一个函数来创建有创世块的区块链：

```rust
    /// Build blockchain
    pub fn new_blockchain() -> BlockChain {
        let genesis_block = BlockChain::new_genesis_block();
        BlockChain {
            blocks: [genesis_block].to_vec(),
        }
    }
```

检查一个我们的区块链是否如期工作：

```rust
fn main() {
    let mut blockchain = BlockChain::new_blockchain();
    blockchain.add_block("Send 1 BTC to Ivan");
    blockchain.add_block("Send 1 BTC to Ivan");
    
    for item in blockchain.blocks {
        println!("Prev Hash:{:?}", hex::encode(item.prev_block_hash));
        println!("Data:{:?}", std::str::from_utf8(&item.data).unwrap());
        println!("Hash:{:?}", hex::encode(item.hash));
        println!();
    }
}
```

输出：

```bash
Prev. hash:
Data: Genesis Block
Hash: aff955a50dc6cd2abfe81b8849eab15f99ed1dc333d38487024223b5fe0f1168

Prev. hash: aff955a50dc6cd2abfe81b8849eab15f99ed1dc333d38487024223b5fe0f1168
Data: Send 1 BTC to Ivan
Hash: d75ce22a840abb9b4e8fc3b60767c4ba3f46a0432d3ea15b71aef9fde6a314e1

Prev. hash: d75ce22a840abb9b4e8fc3b60767c4ba3f46a0432d3ea15b71aef9fde6a314e1
Data: Send 2 more BTC to Ivan
Hash: 561237522bb7fcfbccbc6fe0e98bbbde7427ffe01c6fb223f7562288ca2295d1
```

### 总结

创建了一个非常简单的区块链原型：它仅仅是一个数组构成的一系列区块，每个块都与前一个块相关联。

```bash
Prev Hash:""
Data:"Genesis Block"
Hash:"317d532f89387edffe94d31b6b3d328ec703fd02fe0df6804160506cd490ed25"

Prev Hash:"317d532f89387edffe94d31b6b3d328ec703fd02fe0df6804160506cd490ed25"
Data:"Send 1 BTC to Ivan"
Hash:"bc6227cdcd55a0080cf762466d4a90a1fa17e51d1ee7ccb076a8a493a496a3e0"

Prev Hash:"bc6227cdcd55a0080cf762466d4a90a1fa17e51d1ee7ccb076a8a493a496a3e0"
Data:"Send 1 BTC to Ivan"
Hash:"5be94996b6cbb969662f9b45c0025dc16230392f97272fea7c632e257ec2733a"
```

### Rust代码

[Proof-Of-Work](https://jeiwan.net/posts/building-blockchain-in-go-part-2/)
----------

目前所完成的区块链原型，已经可以通过**链式关系把区块**相互关联起来：每个块都与前一个块相关联。

但是，当前实现的区块链有一个巨大的缺陷：向链中加入区块太容易，也太廉价了。而区块链和比特币的其中一个核心就是，要想加入新的区块，必须先完成一些非常困难的工作。



### 工作量证明

区块链的一个关键点就是，一个人必须经过一系列困难的工作，才能将数据放入到区块链中。正是由于这种困难的工作，才保证了区块链的安全和一致。此外，完成这个工作的人，也会获得相应奖励（这也就是通过挖矿获得币）。。

整个 “努力工作并进行证明” 的机制，就叫做工作量证明（proof-of-work）。要想完成工作非常地不容易，因为这需要大量的计算能力：即便是高性能计算机，也无法在短时间内快速完成。另外，这个工作的困难度会随着时间不断增长，以保持每 10 分钟出 1 个新块的速度。**在比特币中，这个工作就是找到一个块的哈希**，同时这个哈希满足了一些必要条件。这个哈希，也就充当了证明的角色。因此，寻求证明（寻找有效哈希），就是矿工实际要做的事情。

### 哈希计算

**获得指定数据的一个哈希值的过程，就叫做哈希计算。**一个哈希，就是对所计算数据的一个唯一表示。对于一个哈希函数，输入任意大小的数据，它会输出一个固定大小的哈希值。下面是哈希的几个关键特性：

1. 无法从一个哈希值恢复原始数据。也就是说，哈希并不是加密。
2. 对于特定的数据，只能有一个哈希，并且这个哈希是唯一的。
3. 即使是仅仅改变输入数据中的一个字节，也会导致输出一个完全不同的哈希。

![](https://jeiwan.net/images/hashing-example.png)

**哈希函数被广泛用于检测数据的一致性。**

**在区块链中，哈希被用于保证一个块的一致性**。哈希算法的输入数据包含了前一个块的哈希，因此使得不太可能（或者，至少很困难）去修改链中的一个块：因为如果一个人想要修改前面一个块的哈希，那么他必须要重新计算这个块以及后面所有块的哈希。

### Hashcash

比特币使用 [Hashcash](https://en.wikipedia.org/wiki/Hashcash) ，一个最初用来防止垃圾邮件的工作量证明算法。它可以被分解为以下步骤：

1. 取一些公开的数据（比如，如果是 email 的话，它可以是接收者的邮件地址；在比特币中，它是区块头）
2. 给这个公开数据添加一个计数器。计数器默认从 0 开始
3. 将  **data(数据)** 和 **counter(计数器)** 组合到一起，获得一个哈希
4. 检查哈希是否符合一定的条件：
   1. 如果符合条件，结束
   2. 如果不符合，增加计数器，重复步骤 3-4

因此，这是一个暴力算法：改变计数器，计算新的哈希，检查，增加计数器，计算哈希，检查，如此往复。这也是为什么说它的计算成本很高，因为这一步需要如此反复不断地计算和检查。

现在，让我们来仔细看一下一个哈希要满足的必要条件。在原始的 Hashcash 实现中，它的要求是 “一个哈希的前 20 位必须是 0”。在比特币中，这个要求会随着时间而不断变化。因为按照设计，必须保证每 10 分钟生成一个块，而不论计算能力会随着时间增长，或者是会有越来越多的矿工进入网络，所以需要动态调整这个必要条件。

为了阐释这一算法，我从前一个例子（“I like donuts”）中取得数据，并且找到了一个前 3 个字节是全是 0 的哈希。

![](https://github.com/liuchengxu/blockchain-tutorial/raw/master/content/images/127313-98fa6d44aad3701f.png)

 **ca07ca** 是计数器的 16 进制值，十进制的话是 13240266.

### 实现

好了，完成了理论层面，来动手写代码吧！首先，定义挖矿的难度值：

```go
const TARGET_BITS:&str=24;
```

在比特币中，当一个块被挖出来以后，**“target bits” 代表了区块头里存储的难度，也就是开头有多少个 0。**这里的 24 指的是算出来的哈希前 24 位必须是 0，如果用 16 进制表示，就是前 6 位必须是 0，这一点从最后的输出可以看出来。目前我们并不会实现一个动态调整目标的算法，所以将难度定义为一个全局的常量即可。

24 其实是一个可以任意取的数字，其目的只是为了有一个目标（target）而已，这个目标占据不到 256 位的内存空间。同时，我们想要有足够的差异性，但是又不至于大的过分，因为差异性越大，就越难找到一个合适的哈希。

```rust

pub struct ProofOfWork {
    pub block: Block,
    pub target: BigUint,
}

impl ProofOfWork {
    pub fn new(b: Block) -> ProofOfWork {
        let target = BigUint::one() << (256 - TARGET_BITS);
        ProofOfWork { block: b, target }
    }
}
```

   

`let target = BigUint::one() << (256 - target_bits);` 这一行什么意思

这行代码用于计算工作量证明中的目标条件 `target`。

1. `BigUint::one()`: 这是 `num-bigint` 库中的一个函数，用于创建一个值为 1 的大整数 (BigUint) 对象。
2. `<<`: 这是左移位运算符，用于将一个数左移指定的位数。
3. `(256 - target_bits)`: 这部分是计算要左移的位数。在工作量证明中，目标条件的难度通常是通过指定的 `target_bits` 来控制的。`target_bits` 表示要左移的位数，根据工作量证明难度，通常较小的 `target_bits` 表示更高的难度。

因此，这行代码的含义是：创建一个大整数 `BigUint` 对象，其值为 1，并将其左移 `256 - target_bits` 位。这个操作会创建一个目标条件，要求挖矿的结果哈希值必须小于这个目标条件才能被接受。左移操作会使目标条件变得更难以满足，因为左移位数越大，目标条件的值就越小，要求的哈希值就越难以产生。这是工作量证明中控制难度的一种常见方式。



这里，我们构造了 **ProofOfWork** 结构，里面存储了指向一个块(`block`)和一个目标(`target`)的指针。这里的 “目标” ，也就是前一节中所描述的必要条件。这里使用了一个 [大整数](https://golang.org/pkg/math/big/) ，我们会将哈希与目标进行比较：先把哈希转换成一个大整数，然后检测它是否小于目标。

在 **NewProofOfWork** 函数中，我们将 **big.Int** 初始化为 1，然后左移 `256 - targetBits` 位。**256** 是一个 SHA-256 哈希的位数，我们将要使用的是 SHA-256 哈希算法。**target（目标）** 的 16 进制形式为：

```
0x10000000000000000000000000000000000000000000000000000000000
```

它在内存上占据了 29 个字节。下面是与前面例子哈希的形式化比较：

```
0fac49161af82ed938add1d8725835cc123a1a87b1b196488360e58d4bfb51e3
0000010000000000000000000000000000000000000000000000000000000000
0000008b0f41ec78bab747864db66bcb9fb89920ee75f43fdaaeb5544f7f76ca
```

第一个哈希（基于 “I like donuts” 计算）比目标要大，因此它并不是一个有效的工作量证明。第二个哈希（基于 “I like donutsca07ca” 计算）比目标要小，所以是一个有效的证明。



现在，我们需要有数据来进行哈希，准备数据：

```rust

    /// Prepare for Hash
    fn prepare_data(&self, nonce: i64) -> Vec<u8> {
        let mut data = Vec::new();

        // add PrevBlockHash、Data、Timestamp、targetBits and nonce into data
        data.extend_from_slice(&self.block.prev_block_hash);
        data.extend_from_slice(&self.block.data);
        data.extend_from_slice(&int_to_hex(self.block.timestamp.try_into().unwrap()));
        data.extend_from_slice(&int_to_hex(TARGET_BITS as i64));
        data.extend_from_slice(&int_to_hex(nonce));

        data
    }

```

这个部分比较直观：只需要将 target ，nonce 与 Block 进行合并。这里的 `nonce`，就是上面 Hashcash 所提到的计数器，它是一个密码学术语。

很好，到这里，所有的准备工作就完成了，下面来实现 PoW 算法的核心：

```rust
    /// PoW
    pub fn run(&mut self) -> (u64, Vec<u8>) {
        let mut nonce: u64 = 0;

        println!(
            "Mining the block containing {:?}",
            String::from_utf8_lossy(&self.block.data.clone())
        );

        loop {
            let data = self.prepare_data(nonce.try_into().unwrap());
            let hash = Sha256::digest(&data);
            let hash_int = BigUint::from_bytes_be(&hash);

            if hash_int < self.target {
                println!("Found valid hash: {:?}", hex::encode(hash));
                return (nonce, hash.to_vec());
            } else {
                nonce += 1;
            }
        }
    }
```

首先我们对变量进行初始化：

- `HashInt` 是 `hash` 的整形表示；
- `nonce` 是计数器。

然后开始一个 “无限” 循环：`maxNonce` 对这个循环进行了限制, 它等于 `math.MaxInt64`，这是为了避免 `nonce` 可能出现的溢出。尽管我们 PoW 的难度很小，以至于计数器其实不太可能会溢出，但最好还是以防万一检查一下。

在这个循环中，我们做的事情有：

1. 准备数据
2. 用 SHA-256 对数据进行哈希
3. 将哈希转换成一个大整数
4. 将这个大整数与目标进行比较

跟之前所讲的一样简单。现在我们可以移除 `Block` 的 `SetHash` 方法，然后修改 `NewBlock` 函数：

```rust
func NewBlock(data string, prevBlockHash []byte) *Block {
	block := &Block{time.Now().Unix(), []byte(data), prevBlockHash, []byte{}, 0}
	pow := NewProofOfWork(block)
	nonce, hash := pow.Run()

	block.Hash = hash[:]
	block.Nonce = nonce

	retu   /// Create a new block
    pub fn new_block(data: &str, prev_block_hash: Vec<u8>) -> Block {
        // get timestamp
        let timestamp = SystemTime::now()
            .duration_since(UNIX_EPOCH)
            .unwrap()
            .as_secs();

        // Clone prev_block_hash
        let prev_block_hash_clone = prev_block_hash.clone();

        let block = Block::new(
            timestamp,
            data.to_string().into_bytes(),
            prev_block_hash,
            [].to_vec(),
            0,
        );

        let block_clone = block.clone();
        let mut pow = ProofOfWork::new(block_clone);

        let (nonce, hash) = pow.run();

        Block {
            timestamp,
            data: data.as_bytes().to_vec(),
            prev_block_hash: prev_block_hash_clone, // Use the cloned value here
            hash: hash.to_vec(),
            nonce,
        }
    }rn block
}
```

在这里，你可以看到 `nonce` 被保存为 `Block` 的一个属性。这是十分有必要的，因为待会儿我们对这个工作量进行验证时会用到 `nonce` 。`Block` 结构现在看起来像是这样：

```rust
#[derive(Clone)]
/// Block
pub struct Block {
    pub timestamp: u64,
    pub data: Vec<u8>,
    pub prev_block_hash: Vec<u8>,
    pub hash: Vec<u8>,
    pub nonce: u64,
}
```



还剩下一件事情需要做，对工作量证明进行验证：

```rust
    pub fn validate(&self) -> bool {
        let data = self.prepare_data(self.block.nonce.try_into().unwrap());
        let hash = Sha256::digest(data);
        let hash_int = BigUint::from_bytes_be(&hash);

        hash_int < self.target
    }
```

这里，就是我们就用到了上面保存的 `nonce`。

再来检测一次是否正常工作：

```go
fn main() {
    let mut blockchain = BlockChain::new_blockchain();
    blockchain.add_block("Send 1 BTC to Ivan");
    blockchain.add_block("Send 1 BTC to Ivan");
    
    for item in &blockchain.blocks {
        println!("Prev Hash:{:?}", hex::encode(&item.prev_block_hash));
        println!("Data:{:?}", std::str::from_utf8(&item.data).unwrap());
        println!("Hash:{:?}", hex::encode(&item.hash));
        let pow = ProofOfWork::new(item.clone());
        println!("Pow:{:?}", pow.validate());
    
        println!();
    }
    
}

```

输出：

```bash
Mining the block containing "Genesis Block"
Found valid hash: "000000529ee5cfc4c0de6671f3f00b1cd80751dda24457eea775cd624b6cf926"
Mining the block containing "Send 1 BTC to Ivan"
Found valid hash: "00000033779efeac2662e8e5f6984a98af463a882a641ed1827fce686c62c1c4"
Mining the block containing "Send 1 BTC to Ivan"
Found valid hash: "000000104de8292c8a47d3bf09394252220a34861127be2f3eeafbe386715fb2"
Prev Hash:""
Data:"Genesis Block"
Hash:"000000529ee5cfc4c0de6671f3f00b1cd80751dda24457eea775cd624b6cf926"
Pow:true

Prev Hash:"000000529ee5cfc4c0de6671f3f00b1cd80751dda24457eea775cd624b6cf926"
Data:"Send 1 BTC to Ivan"
Hash:"00000033779efeac2662e8e5f6984a98af463a882a641ed1827fce686c62c1c4"
Pow:true

Prev Hash:"00000033779efeac2662e8e5f6984a98af463a882a641ed1827fce686c62c1c4"
Data:"Send 1 BTC to Ivan"
Hash:"000000104de8292c8a47d3bf09394252220a34861127be2f3eeafbe386715fb2"
Pow:true
```





### 总结

我们离真正的区块链又进了一步：现在需要经过一些困难的工作才能加入新的块，因此挖矿就有可能了。但是，它仍然缺少一些至关重要的特性：区块链数据库并不是持久化的，没有钱包，地址，交易，也没有共识机制。

## [Persistence and CLI](https://jeiwan.net/posts/building-blockchain-in-go-part-3/)



### 引言

到目前为止，我们已经构建了一个有工作量证明机制的区块链。有了工作量证明，挖矿也就有了着落。虽然目前距离一个有着完整功能的区块链越来越近了，但是它仍然缺少了一些重要的特性。在今天的内容中，我们会将区块链持久化到一个数据库中，然后会提供一个简单的命令行接口，用来完成一些与区块链的交互操作。本质上，区块链是一个分布式数据库，不过，我们暂时先忽略 “分布式” 这个部分，仅专注于 “存储” 这一点。

### 选择数据库

目前，我们的区块链实现里面并没有用到数据库，而是在每次运行程序时，简单地将区块链存储在内存中。那么一旦程序退出，所有的内容就都消失了。我们没有办法再次使用这条链，也没有办法与其他人共享，所以我们需要把它存储到磁盘上。

那么，我们要用哪个数据库呢？实际上，任何一个数据库都可以。在 [比特币原始论文](https://bitcoin.org/bitcoin.pdf) 中，并没有提到要使用哪一个具体的数据库，它完全取决于开发者如何选择。 [Bitcoin Core](https://github.com/bitcoin/bitcoin) ，最初由中本聪发布，现在是比特币的一个参考实现，它使用的是  [LevelDB](https://github.com/google/leveldb)。而我们将要使用的是...

### BoltDB

因为它：

1. 非常简洁
2. 用 Go 实现
3. 不需要运行一个服务器
4. 能够允许我们构造想要的数据结构

BoltDB GitHub 上的 [README](https://github.com/boltdb/bolt) 是这么说的：

>Bolt 是一个纯键值存储的 Go 数据库，启发自 Howard Chu 的 LMDB. 它旨在为那些无须一个像 Postgres 和 MySQL 这样有着完整数据库服务器的项目，提供一个简单，快速和可靠的数据库。
>
>由于 Bolt 意在用于提供一些底层功能，简洁便成为其关键所在。它的 API 并不多，并且仅关注值的获取和设置。仅此而已。

听起来跟我们的需求完美契合！来快速过一下：

Bolt 使用键值存储，这意味着它没有像 SQL RDBMS （MySQL，PostgreSQL 等等）的表，没有行和列。相反，数据被存储为键值对（key-value pair，就像 Golang 的 map）。键值对被存储在 bucket 中，这是为了将相似的键值对进行分组（类似 RDBMS 中的表格）。因此，为了获取一个值，你需要知道一个 bucket 和一个键（key）。

需要注意的一个事情是，Bolt 数据库没有数据类型：键和值都是字节数组（byte array）。鉴于需要在里面存储 Go 的结构（准确来说，也就是存储**Block（块）**），我们需要对它们进行序列化，也就说，实现一个从 Go struct 转换到一个 byte array 的机制，同时还可以从一个 byte array 再转换回 Go struct。虽然我们将会使用  [encoding/gob](https://golang.org/pkg/encoding/gob/)  来完成这一目标，但实际上也可以选择使用 **JSON**, **XML**, **Protocol Buffers** 等等。之所以选择使用 **encoding/gob**, 是因为它很简单，而且是 Go 标准库的一部分。

虽然 BoltDB 的作者出于个人原因已经不在对其维护（见[README](https://github.com/boltdb/bolt/commit/fa5367d20c994db73282594be0146ab221657943)）, 不过关系不大，它已经足够稳定了，况且也有活跃的 fork:[coreos/bblot](https://github.com/coreos/bbolt)。

## 数据库结构

在开始实现持久化的逻辑之前，我们首先需要决定到底要如何在数据库中进行存储。为此，我们可以参考 Bitcoin Core 的做法：

简单来说，Bitcoin Core 使用两个 “bucket” 来存储数据：

1. 其中一个 bucket 是 **blocks**，它存储了描述一条链中所有块的元数据
2. 另一个 bucket 是 **chainstate**，存储了一条链的状态，也就是当前所有的未花费的交易输出，和一些元数据

此外，出于性能的考虑，Bitcoin Core 将每个区块（block）存储为磁盘上的不同文件。如此一来，就不需要仅仅为了读取一个单一的块而将所有（或者部分）的块都加载到内存中。但是，为了简单起见，我们并不会实现这一点。

在 **blocks** 中，**key -> value** 为：

|                        key                         |                        value                        |
| :------------------------------------------------: | :-------------------------------------------------: |
|             `b` + 32 字节的 block hash             |                 block index record                  |
|             `f` + 4 字节的 file number             |               file information record               |
|             `l` + 4 字节的 file number             |           the last block file number used           |
|               `R` + 1 字节的 boolean               |                  是否正在 reindex                   |
| `F` + 1 字节的 flag name length + flag name string | 1 byte boolean: various flags that can be on or off |
|          `t` + 32 字节的 transaction hash          |              transaction index record               |

在 **chainstate**，**key -> value** 为：

|               key                |                            value                             |
| :------------------------------: | :----------------------------------------------------------: |
| `c` + 32 字节的 transaction hash |    unspent transaction output record for that transaction    |
|               `B`                | 32 字节的 block hash: the block hash up to which the database represents the unspent transaction outputs |

详情可见 **[这里](https://en.bitcoin.it/wiki/Bitcoin_Core_0.11_(ch_2):_Data_Storage)**。

因为目前还没有交易，所以我们只需要 **blocks** bucket。另外，正如上面提到的，我们会将整个数据库存储为单个文件，而不是将区块存储在不同的文件中。所以，我们也不会需要文件编号（file number）相关的东西。最终，我们会用到的键值对有：

1. 32 字节的 block-hash -> block 结构
2. `l` -> 链中最后一个块的 hash

这就是实现持久化机制所有需要了解的内容了。

## 序列化

上面提到，在 BoltDB 中，值只能是 `[]byte` 类型，但是我们想要存储 `Block` 结构。所以，我们需要使用 [encoding/gob](https://golang.org/pkg/encoding/gob/) 来对这些结构进行序列化。

让我们来实现 `Block` 的 `Serialize` 方法（为了简洁起见，此处略去了错误处理）：

```go
func (b *Block) Serialize() []byte {
	var result bytes.Buffer
	encoder := gob.NewEncoder(&result)

	err := encoder.Encode(b)

	return result.Bytes()
}
```

这个部分比较直观：首先，我们定义一个 buffer 存储序列化之后的数据。然后，我们初始化一个 gob `encoder` 并对 block 进行编码，结果作为一个字节数组返回。

接下来，我们需要一个解序列化的函数，它会接受一个字节数组作为输入，并返回一个 `Block`. 它不是一个方法（method），而是一个单独的函数（function）：

```go
func DeserializeBlock(d []byte) *Block {
	var block Block

	decoder := gob.NewDecoder(bytes.NewReader(d))
	err := decoder.Decode(&block)

	return &block
}
```

这就是序列化部分的内容了。

## 持久化

让我们从 `NewBlockchain` 函数开始。在之前的实现中，`NewBlockchain` 会创建一个新的 `Blockchain` 实例，并向其中加入创世块。而现在，我们希望它做的事情有：

1. 打开一个数据库文件
2. 检查文件里面是否已经存储了一个区块链
3. 如果已经存储了一个区块链：
    1. 创建一个新的 `Blockchain` 实例
    2. 设置 `Blockchain` 实例的 tip 为数据库中存储的最后一个块的哈希
4. 如果没有区块链：
    1. 创建创世块
    2. 存储到数据库
    3. 将创世块哈希保存为最后一个块的哈希
    4. 创建一个新的 `Blockchain` 实例，初始时 tip 指向创世块（tip 有尾部，尖端的意思，在这里 tip 存储的是最后一个块的哈希）

代码大概是这样：

```go
func NewBlockchain() *Blockchain {
	var tip []byte
	db, err := bolt.Open(dbFile, 0600, nil)

	err = db.Update(func(tx *bolt.Tx) error {
		b := tx.Bucket([]byte(blocksBucket))

		if b == nil {
			genesis := NewGenesisBlock()
			b, err := tx.CreateBucket([]byte(blocksBucket))
			err = b.Put(genesis.Hash, genesis.Serialize())
			err = b.Put([]byte("l"), genesis.Hash)
			tip = genesis.Hash
		} else {
			tip = b.Get([]byte("l"))
		}

		return nil
	})

	bc := Blockchain{tip, db}

	return &bc
}
```

来一段一段地看下代码：

```go
db, err := bolt.Open(dbFile, 0600, nil)
```

这是打开一个 BoltDB 文件的标准做法。注意，即使不存在这样的文件，它也不会返回错误。

```go
err = db.Update(func(tx *bolt.Tx) error {
...
})
```

在 BoltDB 中，数据库操作通过一个事务（transaction）进行操作。有两种类型的事务：只读（read-only）和读写（read-write）。这里，打开的是一个读写事务（`db.Update(...)`），因为我们可能会向数据库中添加创世块。

```go
b := tx.Bucket([]byte(blocksBucket))

if b == nil {
	genesis := NewGenesisBlock()
	b, err := tx.CreateBucket([]byte(blocksBucket))
	err = b.Put(genesis.Hash, genesis.Serialize())
	err = b.Put([]byte("l"), genesis.Hash)
	tip = genesis.Hash
} else {
	tip = b.Get([]byte("l"))
}
```

这里是函数的核心。在这里，我们先获取了存储区块的 bucket：如果存在，就从中读取 `l` 键；如果不存在，就生成创世块，创建 bucket，并将区块保存到里面，然后更新 `l` 键以存储链中最后一个块的哈希。

另外，注意创建 `Blockchain` 一个新的方式：

```go
bc := Blockchain{tip, db}
```

这次，我们不在里面存储所有的区块了，而是仅存储区块链的 `tip`。另外，我们存储了一个数据库连接。因为我们想要一旦打开它的话，就让它一直运行，直到程序运行结束。因此，`Blockchain` 的结构现在看起来是这样：

```go
type Blockchain struct {
	tip []byte
	db  *bolt.DB
}
```

接下来我们想要更新的是 `AddBlock` 方法：现在向链中加入区块，就不是像之前向一个数组中加入一个元素那么简单了。从现在开始，我们会将区块存储在数据库里面：

```go
func (bc *Blockchain) AddBlock(data string) {
	var lastHash []byte

	err := bc.db.View(func(tx *bolt.Tx) error {
		b := tx.Bucket([]byte(blocksBucket))
		lastHash = b.Get([]byte("l"))

		return nil
	})

	newBlock := NewBlock(data, lastHash)

	err = bc.db.Update(func(tx *bolt.Tx) error {
		b := tx.Bucket([]byte(blocksBucket))
		err := b.Put(newBlock.Hash, newBlock.Serialize())
		err = b.Put([]byte("l"), newBlock.Hash)
		bc.tip = newBlock.Hash

		return nil
	})
}
```

继续来一段一段分解开来：

```go
err := bc.db.View(func(tx *bolt.Tx) error {
	b := tx.Bucket([]byte(blocksBucket))
	lastHash = b.Get([]byte("l"))

	return nil
})
```

这是 BoltDB 事务的另一个类型（只读）。在这里，我们会从数据库中获取最后一个块的哈希，然后用它来挖出一个新的块的哈希：

```go
newBlock := NewBlock(data, lastHash)
b := tx.Bucket([]byte(blocksBucket))
err := b.Put(newBlock.Hash, newBlock.Serialize())
err = b.Put([]byte("l"), newBlock.Hash)
bc.tip = newBlock.Hash
```

## 检查区块链

现在，产生的所有块都会被保存到一个数据库里面，所以我们可以重新打开一个链，然后向里面加入新块。但是在实现这一点后，我们失去了之前一个非常好的特性：再也无法打印区块链的区块了，因为现在不是将区块存储在一个数组，而是放到了数据库里面。让我们来解决这个问题！

BoltDB 允许对一个 bucket 里面的所有 key 进行迭代，但是所有的 key 都以字节序进行存储，而且我们想要以区块能够进入区块链中的顺序进行打印。此外，因为我们不想将所有的块都加载到内存中（因为我们的区块链数据库可能很大！或者现在可以假装它可能很大），我们将会一个一个地读取它们。故而，我们需要一个区块链迭代器（`BlockchainIterator`）：

```go
type BlockchainIterator struct {
	currentHash []byte
	db          *bolt.DB
}
```

每当要对链中的块进行迭代时，我们就会创建一个迭代器，里面存储了当前迭代的块哈希（`currentHash`）和数据库的连接（`db`）。通过 `db`，迭代器逻辑上被附属到一个区块链上（这里的区块链指的是存储了一个数据库连接的 `Blockchain` 实例），并且通过 `Blockchain` 方法进行创建：

```go
func (bc *Blockchain) Iterator() *BlockchainIterator {
	bci := &BlockchainIterator{bc.tip, bc.db}

	return bci
}
```

注意，迭代器的初始状态为链中的 tip，因此区块将从尾到头（创世块为头），也就是从最新的到最旧的进行获取。实际上，**选择一个 tip 就是意味着给一条链“投票”**。一条链可能有多个分支，最长的那条链会被认为是主分支。在获得一个 tip （可以是链中的任意一个块）之后，我们就可以重新构造整条链，找到它的长度和需要构建它的工作。这同样也意味着，一个 tip 也就是区块链的一种标识符。

`BlockchainIterator` 只会做一件事情：返回链中的下一个块。

```go
func (i *BlockchainIterator) Next() *Block {
	var block *Block

	err := i.db.View(func(tx *bolt.Tx) error {
		b := tx.Bucket([]byte(blocksBucket))
		encodedBlock := b.Get(i.currentHash)
		block = DeserializeBlock(encodedBlock)

		return nil
	})

	i.currentHash = block.PrevBlockHash

	return block
}
```

这就是数据库部分的内容了！

## CLI

到目前为止，我们的实现还没有提供一个与程序交互的接口：目前只是在 `main` 函数中简单执行了 `NewBlockchain` 和 `bc.AddBlock` 。是时候改变了！现在我们想要拥有这些命令：

```go
blockchain_go addblock "Pay 0.031337 for a coffee"
blockchain_go printchain
```

所有命令行相关的操作都会通过 `CLI` 结构进行处理：

```go
type CLI struct {
	bc *Blockchain
}
```

它的 “入口” 是 `Run` 函数：

```go
func (cli *CLI) Run() {
	cli.validateArgs()

	addBlockCmd := flag.NewFlagSet("addblock", flag.ExitOnError)
	printChainCmd := flag.NewFlagSet("printchain", flag.ExitOnError)

	addBlockData := addBlockCmd.String("data", "", "Block data")

	switch os.Args[1] {
	case "addblock":
		err := addBlockCmd.Parse(os.Args[2:])
	case "printchain":
		err := printChainCmd.Parse(os.Args[2:])
	default:
		cli.printUsage()
		os.Exit(1)
	}

	if addBlockCmd.Parsed() {
		if *addBlockData == "" {
			addBlockCmd.Usage()
			os.Exit(1)
		}
		cli.addBlock(*addBlockData)
	}

	if printChainCmd.Parsed() {
		cli.printChain()
	}
}
```

我们会使用标准库里面的 [flag](https://golang.org/pkg/flag/) 包来解析命令行参数：

```go
addBlockCmd := flag.NewFlagSet("addblock", flag.ExitOnError)
printChainCmd := flag.NewFlagSet("printchain", flag.ExitOnError)
addBlockData := addBlockCmd.String("data", "", "Block data")
```

首先，我们创建两个子命令: `addblock` 和 `printchain`, 然后给 `addblock` 添加 `-data` 标志。`printchain` 没有任何标志。

```go
switch os.Args[1] {
case "addblock":
	err := addBlockCmd.Parse(os.Args[2:])
case "printchain":
	err := printChainCmd.Parse(os.Args[2:])
default:
	cli.printUsage()
	os.Exit(1)
}
```

然后，我们检查用户提供的命令，解析相关的 `flag` 子命令：

```go
if addBlockCmd.Parsed() {
	if *addBlockData == "" {
		addBlockCmd.Usage()
		os.Exit(1)
	}
	cli.addBlock(*addBlockData)
}

if printChainCmd.Parsed() {
	cli.printChain()
}
```

接着检查解析是哪一个子命令，并调用相关函数：

```go
func (cli *CLI) addBlock(data string) {
	cli.bc.AddBlock(data)
	fmt.Println("Success!")
}

func (cli *CLI) printChain() {
	bci := cli.bc.Iterator()

	for {
		block := bci.Next()

		fmt.Printf("Prev. hash: %x\n", block.PrevBlockHash)
		fmt.Printf("Data: %s\n", block.Data)
		fmt.Printf("Hash: %x\n", block.Hash)
		pow := NewProofOfWork(block)
		fmt.Printf("PoW: %s\n", strconv.FormatBool(pow.Validate()))
		fmt.Println()

		if len(block.PrevBlockHash) == 0 {
			break
		}
	}
}
```

这部分内容跟之前的很像，唯一的区别是我们现在使用的是 `BlockchainIterator` 对区块链中的区块进行迭代：

记得不要忘了对 `main` 函数作出相应的修改：

```go
func main() {
	bc := NewBlockchain()
	defer bc.db.Close()

	cli := CLI{bc}
	cli.Run()
}
```

注意，无论提供什么命令行参数，都会创建一个新的链。

这就是今天的所有内容了! 来看一下是不是如期工作：

```go
$ blockchain_go printchain
No existing blockchain found. Creating a new one...
Mining the block containing "Genesis Block"
000000edc4a82659cebf087adee1ea353bd57fcd59927662cd5ff1c4f618109b

Prev. hash:
Data: Genesis Block
Hash: 000000edc4a82659cebf087adee1ea353bd57fcd59927662cd5ff1c4f618109b
PoW: true

$ blockchain_go addblock -data "Send 1 BTC to Ivan"
Mining the block containing "Send 1 BTC to Ivan"
000000d7b0c76e1001cdc1fc866b95a481d23f3027d86901eaeb77ae6d002b13

Success!

$ blockchain_go addblock -data "Pay 0.31337 BTC for a coffee"
Mining the block containing "Pay 0.31337 BTC for a coffee"
000000aa0748da7367dec6b9de5027f4fae0963df89ff39d8f20fd7299307148

Success!

$ blockchain_go printchain
Prev. hash: 000000d7b0c76e1001cdc1fc866b95a481d23f3027d86901eaeb77ae6d002b13
Data: Pay 0.31337 BTC for a coffee
Hash: 000000aa0748da7367dec6b9de5027f4fae0963df89ff39d8f20fd7299307148
PoW: true

Prev. hash: 000000edc4a82659cebf087adee1ea353bd57fcd59927662cd5ff1c4f618109b
Data: Send 1 BTC to Ivan
Hash: 000000d7b0c76e1001cdc1fc866b95a481d23f3027d86901eaeb77ae6d002b13
PoW: true

Prev. hash:
Data: Genesis Block
Hash: 000000edc4a82659cebf087adee1ea353bd57fcd59927662cd5ff1c4f618109b
PoW: true
```



