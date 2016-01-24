什么是面向对象
===

#什么是面向对象
- 什么是面向对象 
 - 什么是收音机
 - 对象是一个整体，对外提供一些操作
- 什么是面向对象
 - 使用对象时，只关注对象提供的功能，不关注其内部细节
- 面向对象是一种通用思想，并非只有编程中能用。

#JS中的面向对象
- 面向对象编程的特点
 - 抽象：
 - 封装：
 - 继承：
  - 多重继承
  - 多态
- 对象的组成
 - 方法--函数：过程，动态的
 - 属性--变量：状态，静态的

```javascript
var arr = [1,2,3,4,5];
alert(arr.length);
```
 
#第一个面向对象的程序
```javascript
//this：当前的方法属于谁
//1
var arr = [1,2,3];
arr.show=function(){
	alert(this.length);//this指的是arr
};
arr.show();//alert 3

//2
oDiv.onclick=function(){
	alert(this);//oDiv,谁发生事件，this指向谁
    //this：当前的方法属于谁
}

//3
function show(){
	alert(this);//浏览器中是window，node中undifined
}
```

- 创建对象

```javascript
//1-
var obj = new Object();
obj.show = function(){
	alert(this.aaa);
};
obj.show();

//2-
var obj = new Object();
obj.name='blue';
obj.sex='男'；
obj.showName=function(){
	alert("我的名字叫"+this.name);
}
obj.showSex = function(){
	alert('我是'+this.sex);
}
obj.showName();
obj.showSex();

//3-工厂方式创建对象
function createPerson(name,sex){     //构造函数--用工厂方式构造函数
    //1.原料
  	var obj = new Object();
    
    //2.加工
    obj.name = name;
    obj.sex = sex;
    obj.showName=function(){
    	alert('我的名字叫：'+this.name);
    };
    obj.showSex=function(){
    	alert('我是'+this。sex+'的');
    };
	  
    //3.出厂
    return obj;
}

var p1 = createPerson('blue','男');
var p2 = createPerson('leo','女');

/*
工厂方式的缺点：
	1.没有new
	2.每个对象都有自己的函数
*/

```

# new

```javascript
//new的区别
function show(){
	alert(this);
}
show(); //window
new show(); //新创建的对象
```


#原型（prote）
```javascript
//1-给数组添加对象
var arr1 = new Array[1,2,3];
var arr2 = new Array[4,5,6];

arr1.sum = function(){
	var result = 0;
	var i = 0;
  
	for(i=0;i < this.length;i++){
  	 result+=this[i];
	}
  
	return result;
};

//2-给数组的原型添加方法
var arr1 = new Array[1,2,3];
var arr2 = new Array[4,5,6];

Array.prototype.sum=function(){
	 var result = 0;
    var i=0;
    for(i=0;i<this.length;i++){
    	result+=this[i];
    }
    return result;
}

alert(arr1.sum);
alert(arr2.sum);



//3-用原型工厂方式构造对象:用构造函数创建属性，用原型创建方法
function CreatePerson(name,sex){
	this.name=name;
	this.sex=sex;
};

CreatePerson.prototype.showName=function(){
	alert('我的名字叫：'+this.name);
};
CreatePerson.prototype.showSex=function(){
	alert('我是'+this.sex+'的')；
};


//4-原型的优先级
Array.prototype.a = 12;
var arr = [1,2,3];
alert(arr.a);//12

arr.a = 12;
alert(arr.a);//5

delete arr.a;
alert(arr.a);//12

```