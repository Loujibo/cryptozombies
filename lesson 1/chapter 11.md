## 第十一章：事件 Events

我们的合同快完成了！现在让我们添加一个事件。

**事件** 是合约和区块链通讯的一种机制。你的前端应用“监听”某些事件，并做出反应。
例子：
```javascript
//声明一个事件
event IntegersAdded(uint x, uint y, uint result);

function add(uint _x, uint _y) public returns (uint) {
  uint result = _x + _y;
  // 触发一个事件，让应用知道该函数被调用
  emit IntegersAdded(_x, _y, result);
  return result;
}
```
你的 app 前端可以监听这个事件。JavaScript 实现如下:
```javascript
YourContract.IntegersAdded(function(error, result) {
  // ...
})
```