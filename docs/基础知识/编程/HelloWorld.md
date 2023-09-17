# HelloWorld

编译器：[Remix](https://remix.ethereum.org/)

步骤

1. 声明license

```
// SPDX-License-Identifier: MIT
```

2. 声明solidity版本

```
pragma solidity ^0.8.1;
```

3. 创建合约

```
contract HelloWorld{
    
}
```

完整版本

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.1;

contract HelloWorld {
    string public mystring = "hello, world!"; // 字符串会被存储在区块链中
}

```

deploy

![image-20230917175954435](D:/Workplace/github/LearningWeb3.0/docs/基础知识/编程/assets/image-20230917175954435-1694944798939-1.png)

