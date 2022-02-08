## 第六章：函数 Function

在比较老的版本中，solidity 中的函数声明和大多数高级语言一样，如下所示：
```javascript
function eatHamburgers(string _name, uint _amount) public {
}
```
这是一个名为的函数eatHamburgers，它接受 2 个参数： 一个string类型和一个uint了类型的。现在函数的主体是空的。
> 注意：惯例（但不是必需的）以下划线开头的函数参数变量名是为了将它们与全局变量区分开来。我们将在整个教程中使用该约定。

但是在比较新的版本，编译器会报错：

> TypeError: Data location must be "storage", "memory" or "calldata" for parameter in function, but none was given.

google翻译：

> TypeError：函数中参数的数据位置必须是“storage”、“memory”或“calldata”，但没有给出。

这里会涉及到一个**值类型**和**引用类型**的问题（calldata暂时先不做介绍）。

由于solidity没有*号操作符，所以使用以下两个关键字来表示：
***memory（值类型）***
***storage（引用类型）***

**值类型**：值类型传值时，会临时拷贝一份内容出来，而不是拷贝指针，当你修改新的变量时，不会影响原来的变量的值。
> 值类型包含：
>  - 布尔(Booleans)
>  - 整型(Integer)
>  - 地址(Address)
>  - 定长字节数组(fixed byte arrays)
>  - 有理数和整型(Rational and Integer Literals，String literals)
>  - 枚举类型(Enums)
>  - 函数(Function Types)

**引用类型**：引用类型传值时，那么当你修改新变量时，原来变量的值会跟着变化，这是因为新就变量同时指向同一个地址的原因。

> 引用类型包含：
>  - 不定长字节数组（bytes）
>  - 字符串（string）
>  - 数组（Array）
>  - 结构体（Struts）

所以正确的写法是：
```javascript
function eatHamburgers(string memory _name, uint _amount) public {
}
```


你可以这样调用这个函数：
```javascript
eatHamburgers("vitalik", 100);
```