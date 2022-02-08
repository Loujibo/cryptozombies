## 第十章：Keccak256 和 类型转换 Keccak256 and Typecasting

如何让 _generateRandomDna函数返回一个（伪）随机的uint?

Ethereum内部有一个散列函数**keccak256**，它用了SHA3版本。一个散列函数基本上就是把一个字符串转换为一个256位的16进制数字。字符串的一个微小变化会引起散列数据极大变化。

这在 Ethereum 中有很多应用，但是现在我们只是用它造一个（伪）随机数。

例子：
```javascript
//6e91ec6b618bb462a4a6ee5aa2cb0e9cf30f7a052bb467b0ba58b8748c00d2e5
keccak256(abi.encodePacked("aaaab"));
//b1f078126895a1424524de5321b339ab00408010b7cf0e6ed451514981e58aa9
keccak256(abi.encodePacked("aaaac"));
```
显而易见，输入字符串只改变了一个字母，输出就已经天壤之别了。

> 注: 在区块链中安全地产生一个随机数是一个很难的问题， 本例的方法不安全，但是在我们的教程里，算法不是那么重要，已经很好地满足我们的需要了。

## 类型转换

有时你需要变换数据类型。例如:
```javascript
uint8 a = 5;
uint b = 6;
// 将会抛出错误，因为 a * b 返回 uint, 而不是 uint8:
uint8 c = a * b;
// 我们需要将 b 转换为 uint8:
uint8 c = a * uint8(b);
```
上面, a * b 返回类型是 uint, 但是当我们尝试用 uint8 类型接收时, 就会造成潜在的错误。如果把它的数据类型转换为 uint8, 就可以了，编译器也不会出错。

