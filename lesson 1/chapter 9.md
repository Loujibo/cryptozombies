## 第九章：函数的更多属性 More on Functions

本章中我们将学习函数的返回值和修饰符。

## 返回值

要想函数返回一个数值，按如下定义：
```javascript
string greeting = "What's up dog";

function sayHello() public returns (string) {
  return greeting;
}
```
Solidity 里，函数的定义里可包含返回值的数据类型（如本例中 string）。

函数的修饰符
上面的函数实际上没有改变 Solidity 里的状态，它没有改变任何值或者写任何东西。

这种情况下我们可以把函数定义为 view，意味着它只能读取数据不能更改数据：
```javascript
function sayHello() public view returns (string) {}
```
Solidity 还支持 pure 函数，表明这个函数甚至都不访问应用里的数据，例如：
```javascript
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}
```
这个函数甚至都不读取应用里的状态，它的返回值完全取决于它的输入参数，在这种情况下我们把函数定义为 pure。

> 注：可能很难记住何时把函数标记为 pure/view。 幸运的是， Solidity 编辑器会给出提示，提醒你使用这些修饰符。
