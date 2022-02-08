## 第七章：使用结构体和数组 Working With Structs and Arrays

## 创建新的结构体

还记得上个例子中的 Person 结构吗？
```javascript
struct Person {
  uint age;
  string name;
}
Person[] public people;
```
现在我们学习创建新的 Person 结构，然后把它加入到名为 people 的数组中.
```javascript
// 创建一个新的Person:
Person satoshi = Person(172, "Satoshi");

// 将新创建的satoshi添加进people数组:
people.push(satoshi);
```

你也可以两步并一步，用一行代码更简洁:
```javascript
people.push(Person(16, "Vitalik"));
```

> 注：array.push() 在数组的 尾部 加入新元素，所以元素在数组中的顺序就是我们添加的顺序，如:
> 
> ```javascript 
> uint[] numbers; 
> numbers.push(5); 
> numbers.push(10);
> numbers.push(15); 
> // numbers 数组现在是 [5, 10, 15]
>  ```
