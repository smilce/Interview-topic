## 1，考察对对象的理解
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

## 2，考察变量声明
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

## 3，考察this和作用域
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


## 4，考察闭包和对函数的理解
写一个这样的函数sum，输入任意个数字，返回这些数字的和，
并且这个返回的结果仍然可以输入数字在原基础上进行和的累加。如：var a = sum(1,2)，
则 a = 3；同时a仍然可以继续输入数字在原基础上累加，如a(3,4,5)得到15，继续调用
a(6)得到21，以此类推。
var a = sum() // 3;
a(3,4,5) // 15;
a(6) // 21;
function sum(){
    var _nums = [];
    var _sum = function(){
        _nums.push.apply(_nums, Array.prototype.slice.call(arguments));
    }
    _nums.push.apply(_nums, Array.prototype.slice.call(arguments));
    _sum.toString = function(){
        return _nums.reduce(function(prev, arg){
            return prev+arg;
        }, 0)
    }
    return _sum;
}

## 5,考察原型链
写一个函数a，使它的继承结构如下：
a -> {b: 2} -> Array.prototype -> Object.prototype
