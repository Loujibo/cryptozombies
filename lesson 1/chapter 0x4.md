## 第四章：结构体 Structs

有时你需要更复杂的数据类型，比如函数的参数个数遇到上限的时候，Solidity 提供了 结构体:
```javascript
struct Person {
  uint age;
  string name;
}
```
结构体允许你生成一个更复杂的数据类型，它有多个属性。

> 注：我们刚刚引进了一个新类型，string。 字符串用于保存任意长度的 UTF-8 编码数据。 如： string greeting = "Hello world!"。

