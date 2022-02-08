## 第一章：合约 Contracts

Solidity 的代码都包裹在合约里面，合约就是 **以太坊** 应用的基本模块， 所有的变量和函数都属于合约，它是你所有项目的起点。

以下是一份名为 **HelloWorld** 的合约
```javascript
contract HelloWorld {

}
```
## 标题版本指令
所有的 Solidity 源码都必须以 **"pragma solidity"** 开头，用来标明Solidity编译器的版本，以避免你的代码和其他版本的编译器发生冲突。

例如: 
`pragma solidity ^0.8.11；`(使用0.8.11版本的编译器)。
`pragma solidity >=0.7.0 <0.9.0;`(使用0.7.0版本（包含）到0.9.0版本（不包含）的编译器)

综上所述，下面是一个基本合约的代码：
```javascript
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.11;
contract HelloWorld {
}
```
你会发现多了这样一条注释`// SPDX-License-Identifier: GPL-3.0`
如果你不加这条注释，他会有一个警告：
>Warning: SPDX license identifier not provided in source file. Before publishing, consider adding a comment containing "SPDX-License-Identifier: <SPDX-License>" to each source file. Use "SPDX-License-Identifier: UNLICENSED" for non-open-source code. Please see https://spdx.org for more information.

google翻译：
>警告：源文件中未提供 SPDX 许可证标识符。 在发布之前，请考虑将包含“SPDX-License-Identifier: <SPDX-License>”的注释添加到每个源文件。 对非开源代码使用“SPDX-License-Identifier: UNLICENSED”。 请参阅 https://spdx.org 了解更多信息。

这里就不多作说明。