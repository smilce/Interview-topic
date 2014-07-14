### 1，考察对对象的理解

```javascript
window.obj = {
    a: 1
}
var obj2 = obj;
obj2.b = 2;
console.log(obj);
delete(obj);
console.log(obj);
obj2 = {
    a: 1,
    b: 2
}
obj2.c = 3;
console.log(obj);
```

### 2，考察变量声明

```javascript
var a = 2;
function fn(){
    alert(a);
    inner();
    alert(a);
    alert(b);
    var a = 1;
    alert(a);
    function inner(){
        var b = 2;
        alert(a);
        a = 3;
        alert(b);
    }
}
```

### 3，考察this和作用域

```javascript
var a = 1;
var b = {
    a: 2
}
function c(){
    alert('this: ' +this.a);
    alert('a: ' + a);
    this.a = 3;
}
b.c = c;
c();
new c();
b.c = c;
b.c();
var d = b.c;
d();
(function(){d()})();
d.call(null, 4);
```


### 4，考察闭包和对函数的理解以及递推的使用
写一个这样的函数sum，输入任意个数字，返回这些数字的和，
并且这个返回的结果仍然可以输入数字并在原基础上进行和的累加形成新的累加函数。如：var a = sum(1,2)，
则 a = 3，同时a作为一个累加函数，可以传入新的值继续累加形成新函数b，而a保持不变，如没有变量指向这个新的累加函数，则只输出值，a同样保持不变，以此类推，例如：
```javascript
var a = sum(1, 2) // 3; a持有1、2
a(3,4,5) // 15; 用持有的1、2与3、4、5相加，但a持有的值不变，仍然是1、2，此时打印a仍然是3
var b = a(6); // 9 b持有a原有的1、2，再加上6，即b的打印值为9
b + 1; // 10 b的值为9 ，加1等于10
b(6) // 15 在b持有的1、2、6基础上加上，得15，但b持有的值不变 
var c = b(6); //同样得15，b的持有值扔不变，c得到1、2、6、6
c + b + a; // 27
```

### 5,考察原型链
写一个函数a，使它的继承结构如下：
```javascript
a -> {b: 2} -> Array.prototype -> Object.prototype
```

### 6,考察综合应用能力
实现一个简单的css选择器，只需选择id、class、tag，如
```javascript
$('#id1');
$('.class1 span');
$('#id2 .class1 div');
```
