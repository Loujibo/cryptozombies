## 第八章：私有 / 公共函数 Private / Public Functions

Solidity 定义的函数的属性默认为公共。 这就意味着任何一方 (或其它合约) 都可以调用你合约里的函数。

显然，不是什么时候都需要这样，而且这样的合约易于受到攻击。 所以将自己的函数定义为私有是一个好的编程习惯，只有当你需要外部世界调用它时才将它设置为公共。

如何定义一个私有的函数呢？
```javascript
uint[] numbers;

function _addToArray(uint _number) private {
  numbers.push(_number);
}
```
这意味着只有我们合约中的其它函数才能够调用这个函数，给 numbers 数组添加新成员。

可以看到，在函数名字后面使用关键字 private 即可。和函数的参数类似，私有函数的名字用下划线（_）起始。

​