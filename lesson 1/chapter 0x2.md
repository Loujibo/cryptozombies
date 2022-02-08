## 第二章：状态变量和整数 State Variables & Integers

状态变量是被永久的保存在合约里，也就是说他们被写进了 **以太坊** 的 **区块链** 中，简单的理解就像是写入了一个数据库。
举个例子：
```javascript
contract Example {
  // 这个无符号整数将会永久的被保存在区块链中
  uint myUnsignedInteger = 100;
}
```
在上面这个合约中，定义 **myUnsignedInteger** 为 **uint** 类型，并赋值100。

## 无符号整形
**uint** 数据类型是无符号整数，这意味着它的值必须为非负数。 还有一个用于有符号整数的 **int** 数据类型。

>注意：在 Solidity 中，uint 实际上是 uint256 的别名，uint256 是一个 256 位无符号整数。 你可以用更少的位来声明 uint——uint8、uint16、uint32 等。但通常你只想简单地使用 uint，除非在特定情况下，我们将在后面的课程中讨论。