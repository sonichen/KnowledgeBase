vue3和web3.js交互

## vue安装

```
npm install -g @vue/cli
```

```
vue -V
@vue/cli 5.0.8
```

创建项目

```
vue create web3-wallet
```

![image-20231014153451460](assets\image-20231014153451460.png)

进入：http://localhost:8080/

![image-20231014154156073](assets\image-20231014154156073.png)

## Vue3以及Vant介绍使用

### web3相关第三方包

```shell
npm install web3 bip39 ethereumjs-tx@1.3.7 ethereumjs-util ethereumjs-wallet
```

> ethereumjs-tx使用1.3.7版本

### node-polyfill兼容文件配置

1.下载polyfill插件

```
npm install node-polyfill-webpack-plugin -D
```

在vue.config.js中配置

```js
const { defineConfig } = require('@vue/cli-service')
//引入插件
const NodePolyfillWebpackPlugin=require("node-polyfill-webpack-plugin")

module.exports = defineConfig({
  transpileDependencies: true,
  // 插件配置
  configureWebpack: {
    plugins: [
      new NodePolyfillWebpackPlugin()
    ],
  },
})

```



### [vant-ui UI组件库](https://vant-contrib.gitee.io/vant/#/zh-CN)

```
npm i vant
npm i unplugin-vue-components -D
```

在vue.config.js中配置插件

```js
const { defineConfig } = require('@vue/cli-service')
//引入插件
const NodePolyfillWebpackPlugin=require("node-polyfill-webpack-plugin")
// vant
const {VantResolver}=require("unplugin-vue-components/resolvers")
const ComponentsPlugin=require("unplugin-vue-components/webpack")

module.exports = defineConfig({
  transpileDependencies: true,
  // 插件配置
  configureWebpack: {
    plugins: [
      new NodePolyfillWebpackPlugin(),
      ComponentsPlugin({resolvers: [VantResolver()]}),
    ],
  },
})

```

测试app.vue中添加代码

```
<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/>
   -->
   <van-button type="primary">主要按钮</van-button>
<van-button type="success">成功按钮</van-button>
</template>

```

![image-20231014160452718](assets\image-20231014160452718.png)

![image-20231014160647512](assets\image-20231014160647512.png)

### 通过vm配置响应式

```
npm install postcss-px-to-viewport -D
```

## web3连接到以太坊网络（测试网、主网）

1. 什么是Web3

web3是以太坊官方开提供的一个连接以太坊区块链的模块，允许您使用HTTP或IPC与本地或远程以太坊节点进行交互，它包含以太坊生态系统的几乎所有功能。web3模块主要连接以太坊暴露出来的RPC层。开发者利用web3连接RPC层，可以连接任何暴露了RPC接口的节点，从而与区块链交互。web3是一个集合库，支持多种开发语言使用wbe3，其中的JavaScript API叫做web3.js、另外还有web3.py、web3j，web3.js将是我们钱包开发项目的重点。

 

> web3.js开发文档：web3.js - Ethereum JavaScript API — web3.js 1.0.0 documentation
>
> web3.js 中文文档 : web3.js - 以太坊 JavaScript API — web3.js 中文文档 — 登链社区
>
> github地址：https://github.com/web3/web3.js/tree/v1.0.0-beta.34 
>



2. 实例化web3对象

```js
var Web3=require('web3');
var web3=new Web3(Web3.givenProvider||'ws://some.local-or-remote.node:8546')
```

根据API可知需要指定节点地址，我们将ws://some.local-or-remote.node:8546

换成其它连接到以太坊网络的节点的地址，以此来确定连接的以太坊的网络。那么连接到以太坊网络的节点的地址是多少呢？这里我们需要使用到infura。

3. 获取连接到以太坊网络的节点地址

infura提供公开的 Ethereum主网和测试网络节点，到infura.io网站注册后即可获取各个网络的地址。请按照如下步骤获取地址。

**第一步**：打开 infura网站地址：https://infura.io/dashboard，使用邮箱注册后登陆如下所示：

![image-20231014161950496](assets\image-20231014161950496-1697271596917-1.png)

**第二步**：点击上图标记的“create new project”按钮创建一个新项目。然后弹出如下弹框，在输入框输入项目名，如”MyEtherWallet“，然后点击“create project”按钮创建。

**第三步**：然后会显示如下界面，点击下图中的选择框，可以看到提供主网、Kovan测试网络、Ropsten测试网络、Rinkeby测试网络的节点地址。



**第四步**：选择GoerLi测试网络，然后复制地址，将获取到类似这样的地址：

https://kovan.infura.io/v3/d93f......cd67，如下。

![image-20231014162459305](assets\image-20231014162459305.png)

4. 连接到以太坊测试网络

现在将复制的地址替换掉实例化web对象的地址，如下

```
<template>
  <van-button type="primary">主要按钮</van-button>
  <van-button type="success">成功按钮</van-button>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Web3 from 'web3';

var web3 = new Web3(Web3.givenProvider || 'wss://goerli.infura.io/ws/v3/XXXXX')
console.log(web3);

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style lang="less"></style>

```

![image-20231014163536981](assets\image-20231014163536981.png)

连接到以太坊主网与GoerLi测试网络一样的，只需复制主网节点的地址去实例化web3即可。由于在主网上交易需要花费gas，因此我们基于GoerLi测试网络进行开发，后续开发完成后可再切换到主网。在我们开发的项目源码中，我将获取web3实例的代码封装到了myUtils.js文件的getweb3()方法中，用于整个项目统一调用。

## web3高频API

### 账号创建

创建账号需要使用web3.js

```
web3.eth.accounts.create([entropy]);
```

entropy - string可选：是一个随机字符串，作为解锁账号的密码。如果没有传递字符串，就是用random生成随机字符串。

![image-20231014170018910](assets\image-20231014170018910.png)

![image-20231014163934415](assets\image-20231014163934415.png)



```vue
<template>
  <div >api</div>
</template>

<script setup>
 import Web3 from 'web3';
// 实例化web3
var web3 = new Web3(Web3.givenProvider || 'wss://goerli.infura.io/ws/v3/9b2967006bbc48d789b3afe8d4053643')
// 创建账户
const account=web3.eth.accounts.create("123");
console.log(account);
</script>
<style scoped lang='less'>
</style>
```



### 余额获取

```vue
<template>
    <h1>账户信息：</h1>
    <van-divider />
    <p>地址: 0xA55b1C8De4d960D909457F4420bB69fEf1349187</p>
    <p>私钥: 0x1918fd2a7e94ef4ec4280562de49f4aa54b72afa6e80d6ecb100d5e03d492e37</p>
</template>

<script setup>
import Web3 from 'web3';
// 实例化web3
var web3 = new Web3(Web3.givenProvider || 'wss://goerli.infura.io/ws/v3/9b2967006bbc48d789b3afe8d4053643')
// 创建账户
// 每次执行都生成新账号
// const account=web3.eth.accounts.create("123");
// console.log(account.address);
// console.log(account.privateKey);

const address = "0xA55b1C8De4d960D909457F4420bB69fEf1349187";
// 获取余额
// const mount=web3.eth.getBalance(address)
// console.log(mount)
web3.eth.getBalance(address).then((res) => {
    console.log(res)
});
</script>
<style scoped lang='less'></style>
```



### 单位转化

Eth转为wei



wei转为Eth

### Eth转账

```vue
<template>
    <h1>账户信息：</h1>
    <van-divider />
    <!-- <p>地址: 0xA55b1C8De4d960D909457F4420bB69fEf1349187</p>
    <p>私钥: 0x1918fd2a7e94ef4ec4280562de49f4aa54b72afa6e80d6ecb100d5e03d492e37</p> -->
    <p>地址: 0xA55b1C8De4d960D909457F4420bB69fEf1349187</p>
    <p>私钥: 0x1918fd2a7e94ef4ec4280562de49f4aa54b72afa6e80d6ecb100d5e03d492e37</p>
    <h1>转账</h1>
    <van-divider/>
    <van-button type="primary" @click="send">开始转账</van-button>
</template>

<script setup>
import Web3 from 'web3';
import TX from "ethereumjs-tx"

// 实例化web3
var web3 = new Web3(Web3.givenProvider || 'wss://goerli.infura.io/ws/v3/9b2967006bbc48d789b3afe8d4053643')

// 转账
// 1.构建转发数据体
const send= async()=>{
    var address = "0xA55b1C8De4d960D909457F4420bB69fEf1349187";
    var privateKey ="0x1918fd2a7e94ef4ec4280562de49f4aa54b72afa6e80d6ecb100d5e03d492e37";

    // 构建转账参数
    // 获取账户交易次数
    const nounce=await web3.eth.getTransactionCount(address);
    console.log(nounce);
    // 获取预计转账的gas费用
    const gasPrice=await web3.eth.getGasPrice();
    // 转账金额：以wei作为单位
    const value=web3.utils.toWei("0.01", 'ether');
    const rawTx={
        from:address,
        to:"0xb174Eff97638788505B3D7c9532B945086d717f5",
        nounce,
        gasPrice,
        value,
        data:"0x0000"
    };
   
    // //  //////////////////////////////////////
    // //  2. 生成serializedTx
     //通过转账参数计算最终gas费用，并且通过私钥将转账参数进行编码加密
    // 将私钥去除"ox"后进行hex转换
    var privateKey=new Buffer(privateKey.slice(2),"hex");
    // 需要将交易的数据进行预估gas计算，如何将gas值设置到数据参数中
    let gas=await web3.eth.estimateGas(rawTx);
    console.log(gas);
    rawTx.gas=gas;
    // 通过ethereumjs-tx实现私钥加密
    var tx=new TX(rawTx);
    tx.sign(privateKey);
    var serializedTx=tx.serialize();
    //////////////////////////////////////
    // 通过sendSignedTransaction api发送转账交易，并且获取id
    web3.eth
        .sendSignedTransaction("0x"+serializedTx.toString("hex"))
        .on("transactionHash",(txid)=>{
            console.log("交易成功，请在区块链浏览器查看");
            console.log("交易id", txid);
            console.log("https://goerli.etherscan.io/tx/&{txid}");
        })
        .on("receipt",(ret)=>{console.log("receipt")})
        .on("confirmation",(ret=>{console.log("confirmation")}))
        .on("error",(err=>{
            console.log("error"+err);
        }));


    /////////////////////////////////////
}
</script>
<style scoped lang='less'></style>
```



## 账户系统

### 理解密码、私钥、keystore与助记词

#### 密码

密码不是私钥，密码可以进行修改或重置。它主要用途有两个，

一是转账时候的支付密码，

二是用 keystore 导入钱包时需要输入的密码，用于解锁keystore。

在钱包应用程序中，创建账号时需要设定一个密码，这个密码一般要求不少于 8 个字符，为了安全，密码最好设置复杂一点。

#### 私钥

私钥由64位长度的十六进制的字符组成，比如：

0xE4356E49C88C8B7AB370AF7D5C0C54F0261AAA006F6BDE09CD4745CF54E0115A，一个账户只有一个私钥且不能修改，谁拥有私钥就能够掌控该账号的数字货币。通常一个钱包中私钥和公钥是成对出现的，有了私钥，我们就可以通过一定的算法生成公钥，再通过公钥经过一定的算法生成地址，这一过程都是不可逆的，是如何生成的？我们在上一章节中有详细的说明。私钥一定要妥善保管，若被泄漏别人可以通过私钥解锁账号转出你的该账号的数字货币。

在钱包应用程序中，解锁账号后可以导出私钥。

#### Keystore

因为私钥不利于记忆，容易被盗，因此有了Keystore。Keystore常见于以太坊钱包，它并不是私钥，而是将私钥以加密的方式保存为一份 JSON 文件，这份 JSON 文件就是 keystore，所以它就是加密后的私钥。但是Keystore必须配合钱包密码才能使用该账号，所以只有Keystore文件，并不能掌控账号。对于助记词和私钥就不一样了，只要知道助记词或者私钥就能掌控该账号了。

在应用程序中，可以实现解锁账号后生成Keystore文件，支持的钱包有MetaMask、Mist等。

#### 助记词

私钥是64位长度的十六进制的字符，不利于记录且容易记错，所以用算法将一串随机数转化为了一串12 ~ 24个容易记住的单词，方便保存记录。所以有的同学有了下面的结论：

助记词是私钥的另一种表现形式。

还有同学说助记词=私钥，这是不正确的说法，通过助记词可以获取相关联的多个私钥，但是通过其中一个私钥是不能获取助记词的，因此**助记词≠私钥**。

目前只有少数钱包应用程序支持导出助记词，如MetaMask等。通过助记词导入账号也只有少数钱包应用程序支持，如MyEtherWallet、imToken等。

#### **BIP**

要弄清楚助记词与私钥的关系，得清楚BIP协议，是Bitcoin Improvement Proposals的缩写，意思是Bitcoin 的改进建议，用于提出 Bitcoin 的新功能或改进措施。BIP协议衍生了很多的版本，主要有BIP32、BIP39、BIP44。

##### **BIP32**

BIP32是 HD钱包的核心提案，通过种子来生成主私钥，然后派生海量的子私钥和地址，种子是一串很长的随机数。

##### **BIP39**

由于种子是一串很长的随机数，不利于记录，所以我们用算法将种子转化为一串12 ~ 24个的单词，方便保存记录，这就是BIP39，它扩展了 HD钱包种子的生成算法。

##### **BIP44**

BIP44 是在 BIP32 和 BIP43 的基础上增加多币种，提出的层次结构非常全面，它允许处理多个币种，多个帐户，每个帐户有数百万个地址。

在BIP32路径中定义以下5个级别：

`m/purpse'/coin_type'/account'/change/address_index`

- purpose：在BIP43之后建议将常数设置为44'。表示根据BIP44规范使用该节点的子树。
- Coin_type：币种，代表一个主节点（种子）可用于无限数量的独立加密币，如比特币，Litecoin或Namecoin。此级别为每个加密币创建一个单独的子树，避免重用已经在其它链上存在的地址。开发人员可以为他们的项目注册未使用的号码。
- Account：账户，此级别为了设置独立的用户身份可以将所有币种放在一个的帐户中，从0开始按顺序递增。
- Change：常量0用于外部链，常量1用于内部链，外部链用于钱包在外部用于接收和付款。内部链用于在钱包外部不可见的地址，如返回交易变更。
- Address_index：地址索引，按顺序递增的方式从索引0开始编号。

BIP44的规则使得 HD钱包非常强大，用户只需要保存一个种子，就能控制所有币种，所有账户的钱包，因此由BIP39 生成的助记词非常重要，所以一定安全妥善保管，那么会不会被破解呢？如果一个 HD 钱包助记词是 12 个单词，一共有 2048 个单词可能性，那么随机的生成的助记词所有可能性大概是5e+39，因此几乎不可能被破解。

#####  HD钱包(分层钱包)

通过BIP协议生成账号的钱包叫做HD钱包。这个HD钱包，并不是Hardware Wallet硬件钱包，这里的 HD 是Hierarchical Deterministic的缩写，意思是分层确定性，所以HD钱包的全称为比特币分成确定性钱包 。

### 密码、私钥、keystore与助记词的关系

 ![image-20231019094451670](assets\image-20231019094451670.png)

根据单词，配合路径，生成不同的private key

一个private key可以对应一个账户



创建账户需要一个密码

keystore是账户+密码生成出来的

私钥和keystore通过密码加密完成

## 钱包的核心：私钥

基于以上的分析，我们对以太坊钱包的账号系统有了一个很好的认识，那么我们在使用钱包的过程中，该如何保管自己的钱包呢？主要包含以下几种方式：

- 私钥（Private Key）
- Keystore+密码（Keystore+Password）
- 助记词（Mnemonic code）

通过以上三种中的一种方式都可以解锁账号，然后掌控它，所以对于每种方式中的数据都必须妥善包括，如有泄漏，请尽快转移数字资产。

我们可以得到以下总结：

- 通过私钥+密码可以生成keystore，即加密私钥；
- 通过keystore+密码可以获取私钥，即解密keystore。
- 通过助记词根据不同的路径获取不同的私钥，即使用HD钱包将助记词转化成种子来生成主私钥，然后派生海量的子私钥和地址。

可以看出这几种方式的核心其实都是为了获得私钥，然后去解锁账号，因此钱包的核心功能是私钥的创建、存储和使用。

### 创建账户

#### web3直接创建账户

```
web3.eth.accounts.create([entropy]);
```

#### 助记词创建账户

需要使用bip39协议将助记词转换成种子，再通过ethereumjs-wallet库生成hd钱包，根据路径的不同从hd钱包中获取不同的keypair，keypair中就包含有公钥、私钥，再通过ethereumjs-util库将公钥生成地址，从而根据助记词获取所有关联的账号，能获取到公钥、私钥、地址等数据信息。

可见助记词可以获取多个账号私钥，它比私钥重要性更高，必须妥善保管。

HD 钱包和BIP协议的相关概念请查看"04-密码、私钥、keystore与助记词之间的爱恨情仇"章节中助记词的内容。

##### 1.依赖库

需要用到三个库：bip39、ethereumjs-wallet/hdkey、ethereumjs-util。先安装依赖库，cd到项目跟路径运行命令

```
npm i bip39 ethereumjs-wallet ethereumjs-util
```

- [bip39](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fbitcoinjs%2Fbip39)：随机产生新的 mnemonic code，并可以将其转成 binary 的 seed。
- [ethereumjs-wallet](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fethereumjs%2Fethereumjs-wallet)：生成和管理公私钥，下面使用其中 hdkey 子套件来创建 HD 钱包。
- [ethereumjs-util](https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2Fethereumjs%2Fethereumjs-util)：Ethereum 的一个工具库。

 

##### 2.通过助记词创建账户

- 创建助记词

```vue

<script setup>
 import {ref} from 'vue'
 import * as bip39 from 'bip39'// 引入bip39
 
 // 创建助记词
 const mnemonic=bip39.generateMnemonic();
 console.log(mnemonic);
 // saddle visa carry pill mimic water butter receive runway old drop divorce
</script>

<template>
  <div >hello</div>
</template>

<style scoped lang='less'>
</style>
```



- 根据助记词生成密钥对keypair

```vue
//生成密钥对keypair
// const seed=mnemonicToSeed(mnemonic.value);
// console.log(seed);// 返回对象是promise，需要构造函数接收

// 写法1
// mnemonicToSeed(mnemonic.value).then((seed)=>{
//     console.log(seed);//得到一个数组
// });

// 写法2
const genMnemonic=async()=>{
    const seed=await mnemonicToSeed(mnemonic.value);
    const hdWallet=hdkey.fromMasterSeed(seed);
    // `m/purpse'/coin_type'/account'/change/address_index`
    const keypair=hdWallet.derivePath("m/44'/60'/0'/0/0");
    
    //获取私钥
    // 1.获取钱包对象
    const wallet=keypair.getWallet();
    // 2. 获取钱包地址
    const lowerCaseAddress=wallet.getAddressString();// 0x1907d3bfdfcd47fb69079d8a628fe18ad1c35aba
    // 3. 获取钱包校验地址
    const checkAddress=wallet.getChecksumAddressString(); // 0x1907D3bfdFCD47FB69079D8a628FE18AD1C35aBa
    // 4. 获取私钥
    const priKey=wallet.getPrivateKey().toString("hex");// 1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a

};
genMnemonic();//调用
```

总体来说，先通过BIP39的generateMnemonic生成助记词，然后根据生成的助记词生成密钥对。

载入ethereumjs-wallet包（hdkey），先通过BIP39的mnemonicToSeed把助记词生成一个seed，根据seed获取钱包的对象（hdkey），根据分层钱包，生成keypair，然后获取密钥

### 导出账户

之前生成的

```vue
<template>
  <div >助记词</div>
  <p>{{ mnemonic }}</p>
  <p>路径: m/44'/60'/0'/0/0</p>
  <p>账户地址: 0x1907d3bfdfcd47fb69079d8a628fe18ad1c35aba</p>
  <p>账户私钥: 1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a</p>
</template>
```

```vue
    // 导出keystore
    // 方法1，web3.js // TODO: 报错没解决
    // var web3 = new Web3(Web3.givenProvider || 'wss://goerli.infura.io/ws/v3/9b2967006bbc48d789b3afe8d4053643');
    // const keyStore=web3.eth.accounts.encrypt("1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a","111111");
    // console.log(JSON.stringify(keyStore));
    
    // 方法2 wallet钱包对象
    const keyStore=await wallet.toV3("111111");
    console.log(JSON.stringify(keyStore));
```



```json
{"version":3,"id":"4ce30200-53ba-4599-82a9-5c8394f1aa5e","address":"1907d3bfdfcd47fb69079d8a628fe18ad1c35aba","crypto":{"ciphertext":"7b15846f20dc45b7c770aba7187bdbde60b6646fc86c0fe240e30adad5123528","cipherparams":{"iv":"818bbbeffdf68f5a9cba25eb49433298"},"cipher":"aes-128-ctr","kdf":"scrypt","kdfparams":{"dklen":32,"salt":"e287acd0901755e73cc8acc9a894d1fc39f71cbf4a8347a96c0e0df475114cbe","n":262144,"r":8,"p":1},"mac":"d8240b3c7f07b4025777e253665d964368bcc423cc679089a8a1be8e043d1b8b"}}
```

### 通过keystore生成私钥

```
    // 通过keyStore获取私钥
    // 1. web3
    const res =await web3.eth.accounts.decrypt(keyStore,password);
    // {address: '0x1907D3bfdFCD47FB69079D8a628FE18AD1C35aBa', privateKey: '0x1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a', signTransaction: ƒ, sign: ƒ, encrypt: ƒ}
    // 2. wallet
    const my_wallet=await ethwallet.fromV3(keyStore,password);
    const key=my_wallet.getPrivateKey().toString('hex');
    console.log(key);
```

### 导入账户

```
    // 通过私钥获取地址
    const priKey2=Buffer(priKey,"hex");
    const wallet3=ethwallet.fromPrivateKey(priKey2);
    const lowerCaseAddress2=wallet.getAddressString();
```

### 总结

```vue

<script setup>
 import {ref} from 'vue'
 import {generateMnemonic, mnemonicToSeed}  from 'bip39' //bip39
 import ethwallet, {hdkey} from 'ethereumjs-wallet'
import Web3 from 'web3';
 
 // 创建助记词 //每次都运行意味着产生新钱包
//  const mnemonic=generateMnemonic();
//  console.log(mnemonic);
// 模拟之前生成的助记词
const mnemonic=ref("saddle visa carry pill mimic water butter receive runway old drop divorce");
 
//生成密钥对keypair
// const seed=mnemonicToSeed(mnemonic.value);
// console.log(seed);// 返回对象是promise，需要构造函数接收

// 写法1
// mnemonicToSeed(mnemonic.value).then((seed)=>{
//     console.log(seed);//得到一个数组
// });

// 写法2
const genMnemonic=async()=>{
    const seed=await mnemonicToSeed(mnemonic.value);
    const hdWallet=hdkey.fromMasterSeed(seed);
    // `m/purpse'/coin_type'/account'/change/address_index`
    const keypair=hdWallet.derivePath("m/44'/60'/0'/0/0");
    
    //获取私钥
    // 1.获取钱包对象
    const wallet=keypair.getWallet();
    // 2. 获取钱包地址
    const lowerCaseAddress=wallet.getAddressString();// 0x1907d3bfdfcd47fb69079d8a628fe18ad1c35aba
    // 3. 获取钱包校验地址
    const checkAddress=wallet.getChecksumAddressString(); // 0x1907D3bfdFCD47FB69079D8a628FE18AD1C35aBa
    // 4. 获取私钥
    const priKey=wallet.getPrivateKey().toString("hex");// 1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a
    
    // 导出keystore
    const password="111111";
    // 方法1，web3.js // TODO: 报错没解决
    var web3 = new Web3(Web3.givenProvider || 'wss://goerli.infura.io/ws/v3/9b2967006bbc48d789b3afe8d4053643');
    // const keyStore=web3.eth.accounts.encrypt("1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a","111111");
    // console.log(JSON.stringify(keyStore));
    
    // 方法2 wallet钱包对象
    const keyStore=await wallet.toV3(password);
    console.log(JSON.stringify(keyStore));
    // 通过keyStore获取私钥
    // 1. web3
    const res =await web3.eth.accounts.decrypt(keyStore,password);
    // {address: '0x1907D3bfdFCD47FB69079D8a628FE18AD1C35aBa', privateKey: '0x1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a', signTransaction: ƒ, sign: ƒ, encrypt: ƒ}
    // 2. wallet
    const my_wallet=await ethwallet.fromV3(keyStore,password);
    const key=my_wallet.getPrivateKey().toString('hex');
    console.log(key);
    // 通过私钥获取地址
    const priKey2=Buffer(priKey,"hex");
    const wallet3=ethwallet.fromPrivateKey(priKey2);
    const lowerCaseAddress2=wallet.getAddressString();
};  
genMnemonic();//调用
</script>

<template>
  <div >助记词</div>
  <p>{{ mnemonic }}</p>
  <p>路径: m/44'/60'/0'/0/0</p>
  <p>账户地址: 0x1907d3bfdfcd47fb69079d8a628fe18ad1c35aba</p>
  <p>账户私钥: 1f0e5dad743cd91b12f358c9e68677bdb8a043602877553aaeca677895a20a1a</p>
</template>

<style scoped lang='less'>
</style>
```



## 区块链钱包项目流程

![image-20231019110739637](assets\image-20231019110739637.png)



### 项目准备

创建项目

```
vue create web3-wallet-app
```

**web3相关第三方包**

```shell
npm install web3 bip39 ethereumjs-tx@1.3.7 ethereumjs-util ethereumjs-wallet
```

> ethereumjs-tx使用1.3.7版本

**node-polyfill兼容文件配置**

1.下载polyfill插件

```
npm install node-polyfill-webpack-plugin -D
```

在vue.config.js中配置

```js
const { defineConfig } = require('@vue/cli-service')
//引入插件
const NodePolyfillWebpackPlugin=require("node-polyfill-webpack-plugin")

module.exports = defineConfig({
  transpileDependencies: true,
  // 插件配置
  configureWebpack: {
    plugins: [
      new NodePolyfillWebpackPlugin()
    ],
  },
})

```

**[vant-ui UI组件库](https://vant-contrib.gitee.io/vant/#/zh-CN)**

```
npm i vant
npm i unplugin-vue-components -D
```

在vue.config.js中配置插件

```js
const { defineConfig } = require('@vue/cli-service')
//引入插件
const NodePolyfillWebpackPlugin=require("node-polyfill-webpack-plugin")
// vant
const {VantResolver}=require("unplugin-vue-components/resolvers")
const ComponentsPlugin=require("unplugin-vue-components/webpack")

module.exports = defineConfig({
  transpileDependencies: true,
  // 插件配置
  configureWebpack: {
    plugins: [
      new NodePolyfillWebpackPlugin(),
      ComponentsPlugin({resolvers: [VantResolver()]}),
    ],
  },
})

```

App.vue

```

<template>
  <div>hello</div>
</template>

<script setup>
import { ref } from "vue"

</script>

<style lang="less"></style>

```

### 页面构造

思考：用小狐狸的时候，先是提示输入密码，再助记词

![image-20231019131458971](assets\image-20231019131458971.png)

components/Button.vue

```vue

<template>
    <!-- 间距 -->
    <van-space>
        <van-button type="primary" @click="createWallet">创建钱包</van-button>
        <van-button type="success">导入钱包</van-button>
    </van-space>
    <!-- 弹窗 -->
    <van-dialog v-model:show="show" title="请输入密码" show-cancel-button>
        <van-cell-group>
            <van-field v-model="password" type="password" name="密码" label="密码" placeholder="密码" />

        </van-cell-group>


    </van-dialog>
</template>
  
<script setup>
/**
 * 引入
 */
import { ref } from "vue"
import { showDialog } from 'vant';
import "vant/es/dialog/style"

/**
 * 界面变量控制
 */
const show = ref(false);// 弹窗显示
const password = "";
/**
 * 函数
 */
const createWallet = () => {
    show.value = true;
};

</script>
  
<style lang="less"></style>
  
```

App.vue

```vue

<template>
 <ButtonVue></ButtonVue>
</template>

<script setup>
import { ref } from "vue"
import ButtonVue from "./components/Button.vue"


 
</script>

<style lang="less">
body {
  padding:10px
}
</style>

```



### 本地存储

为了方便，模拟存储在本地

#### store2本地存储工具

```
npm i store2
```

```
import store2 from "store2"
store2("walletInfo",walletInfo);
```

![image-20231019140448077](assets\image-20231019140448077.png)





![image-20231019140913901](assets\image-20231019140913901.png)