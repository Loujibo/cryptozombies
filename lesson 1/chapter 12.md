## 第十二章：ZombieFactory

本章通过一段代码和详细的注释，把我们前面所学到的知识全部复习一遍。认真看完每一行。你会有不一样的收获。

```javascript
// SPDX-License-Identifier: GPL-3.0


//标明Solidity编译器的版本为0.8.11
pragma solidity ^0.8.11;
//定义一个叫ZombieFactory的合约
contract ZombieFactory {
    //定义NewZombie事件，参数为：zombieId(uint)，name(string)，和dna(uint)。
    event NewZombie(uint zombieId, string name, uint dna);
    
    //为了保证我们的僵尸的DNA只含有16个字符，我们先造一个uint数据。
    //让它等于10^16。这样一来以后我们可以用模运算符 % 把一个整数变成16位。
    
    //僵尸DNA将由一个十六位数字组成
    uint dnaDigits = 16;
    //建立一个uint类型的变量，名字叫dnaModulus，令其等于10的 dnaDigits 次方。
    uint dnaModulus = 10 ** dnaDigits;
    
    //建立一个struct 命名为 Zombie。
    //Zombie 结构体有两个属性：name (类型为 string)，和 dna (类型为 uint)。
    struct Zombie {
        string name;
        uint dna;
    }
    
    //为了把一个僵尸部队保存在我们的应用里，并且能够让其它应用看到这些僵尸
    //我们需要创建一个数据类型为 Zombie 的结构体数组
    //用 public 修饰，命名为：zombies。
    Zombie[] public zombies;
    
    //在我们的应用里，我们要能创建一些僵尸，定义私有函数createZombie。
    //它有两个参数: _name (类型为string) _dna (类型为uint)。
    //不要忘记使用memory关键字按值传递第一个参数
    function _createZombie(string memory _name, uint _dna) private {
    //创建一个 Zombie，然后把它加入 zombies 数组中。 
    //新创建的僵尸的 name 和 dna，来自于函数的参数。
        zombies.push(Zombie(_name, _dna));
     //数组的长度-1作为僵尸的id
        uint id = zombies.length - 1;
     //触发NewZombie事件
        emit NewZombie(id, _name, _dna);
    }
    
    //我们需要一个辅助函数，它可以从字符串中生成随机 DNA 编号。
    //创建一个 private 函数，命名为 _generateRandomDna。
    //它只接收一个输入变量 _str (类型 string), 返回一个 uint 类型的数值。
    //不要忘记将_str参数设置为memory。
    //此函数只读取我们合约中的一些变量，所以标记为view。
    function _generateRandomDna(string memory _str) private view returns (uint) {
        //用keccak256，结合参数_str生成一个伪随机数,并且转换成uint类型
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        //我们希望我们的 DNA 只有 16 位数长
        //所以应该return是上面计算的数值对 dnaModulus 求余数(%)。
        return rand % dnaModulus;
    }
    
	//创建一个 public 函数，命名为 createRandomZombie。
	//它将被传入一个变量 _name (数据类型是 string)。 
    function createRandomZombie(string memory _name) public {
	    //函数的第一行应该调用 _generateRandomDna 函数，传入 _name 参数。
		//结果保存在一个类型为 uint 的变量里，命名为 randDna。
        uint randDna = _generateRandomDna(_name);
        //第二行调用 _createZombie 函数， 传入参数： _name 和 randDna。
        _createZombie(_name, randDna);
    }

}

```
好了，现在你对solidity有了一个大概的了解了。下面我们看看怎么调用这个合约！
