## 第五章：数组 Arrays

如果你想建立一个集合，可以用 **数组** 这样的数据类型。Solidity 支持两种数组：**静态** 数组和 **动态** 数组:
```javascript
// 固定长度为2的静态数组:
uint[2] fixedArray;
// 固定长度为5的string类型的静态数组:
string[5] stringArray;
// 动态数组，长度不固定，可以动态添加元素:
uint[] dynamicArray;
```
你也可以建立一个 结构体类型的数组 例如，上一章提到的 Person:
```javascript
Person[] people; // 这是动态数组，我们可以不断添加元素
```
记住：状态变量被永久保存在区块链中。所以在你的合约中创建动态数组来保存成结构的数据是非常有用，有点像数据库。

## 公共数组

你可以定义 public 数组，Solidity会自动创建 getter 方法。语法如下:
```javascript
Person[] public people;
```
其它的合约可以从这个数组读取数据（但不能写入数据），这是在合约中存储公共数据的有效方式。