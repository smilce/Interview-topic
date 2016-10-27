##### 1，实现一个不固定宽高的元素垂直居中

##### 2，实现左侧元素高度适应右侧元素高度

如右侧高度为100px，左侧也为100px，右侧为800px，左侧也为800px

##### 3，实现单行文本居中显示，多行文本居左显示，超过3行截断并显示...


##### 4，请写出以下输出内容

```javascript
window.obj = {
    a: 1
}
var obj2 = obj;
obj2.b = 2;
console.log(obj); 
obj2={
    c: 3
}
console.log(obj)
delete(obj); 
console.log(obj);
```

##### 5，请写出以下输出结果

```javascript
var a = 2;
function fn(){
    console.log(a);
    inner();
    console.log(a);
    function inner(){
        a = 3;
        var a = 4;
        console.log(a);
    }
}
fn();
console.log(a);
```

##### 6，请写出以下输出结果

```javascript
var name = 'name';
var person = {
    name: 'person.name'
}
function fn(){
    console.log(this.name);
    this.name = 'fn.name';
}
person.fn = fn;

fn();
console.log(name)
new fn();
person.fn();
(function(){fn()})();
fn.call(null);
```


##### 7,实现一个构造函数Factory，使它的继承关系如下

```javascript
Factory -> 
{ 
    run: function(){ 
        console.log('run') 
    }
} -> 
Array.prototype -> 
Object.prototype
```

##### 8,模拟jquery实现一个选择器函数（只需要把元素返回即可，考虑兼容性）
```javascript
$('#wrap'); // 选出id为wrap的元素
$('.panel span'); //选出class为panel的节点下的元素
$('#wrap .panel div'); // 选出id为wrap下的class为panel的div元素
```

##### 9，按要求实现函数
输入一个节点，返回这个节点到文档最上方的垂直距离（非到浏览器最上方）

##### 10，按要求写出函数的实现
写一个这样的函数sum，输入任意个数字，返回一个特殊的结果，这个结果直接打印可以打印这些数字的和，但这个结果仍然可以作为函数输入数字并在原基础上进行累加，返回结果同样为这样的一个特殊结果，以此类推。例如：
```javascript
var a = sum(1, 2) ;
console.log(a) // 打印结果为1+2的结果3
var b = a(3,4,5) // 同时a还可以作为函数,继续接收参数
console.log(b); // b也是和a一样的特殊结果，此时打印b为：a的结果和新参数的和，即1+2+3+4+5
console.log(a); // 此时打印仍然是3，也就是a的打印值一直不变
var c = b(6);
console.log(c)//c 的结果为a打印值+b打印值+6的和
console.log(c + b + a); // 打印值为a、b、c的和
```
