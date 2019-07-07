# JS基础

## 1、javascript的typeof返回哪些数据类型

string number array object function Boolean undefined 
数组（Array）、日期对象(Date)、正则(RegExp)、 Math =>object 
考点：使用typeof检测数据类型 
扩展：如何检测数组类型？ 
Array.isArray(); 浏览器兼容性：IE9+ 
toString.call([]);//”[object Array]” 
[] instanceof Array 
var arr=[]; 
arr.constructor;//Array

## 2、例举3种强制类型转换和2种隐式类型转换?

强制类型转换：自己通过函数来进行数据类型转换 
举例：（parseInt,parseFloat,Number()） 
隐式类型转换：JS引擎自动帮我们转换的 
举例：==、 console.log()、 alert() 、if() 、+-*/

扩展：通过==比较两边的值是否相等的结果？ 
1==’1’ 
null==undefined

## 3、split() join() 的区别

split()将字符串按照指定的字符分割成一个数组，并返回 
join()将数组用指定的字符连接成一个字符串，并返回

## 4、数组方法pop() push() unshift() shift()

栈方法： 
push()尾部添加，返回 数组长度 
pop()尾部删除，返回 被删除的元素

队列方法： 
unshift()头部添加 ，返回 数组长度 
shift()头部删除，返回被删除的元素

## 5、事件绑定和普通事件有什么区别

普通事件：给html元素添加一个特定的属性（比如：onclick） 
事件绑定：js代码中通过标记(id tag class)获取元素，给元素添加特定的方法(比如onclick) 
传统事件绑定和符合W3C标准的事件绑定有什么区别？ 
div1.onclick=function(){}; 

1、如果说给同一个元素绑定了两次或者多次相同类型的事件，那么后面的绑定会覆盖前面的绑定 
2、不支持DOM事件流 事件捕获阶段目标元素阶段=>事件冒泡阶段

addEventListener 
1、如果说给同一个元素绑定了两次或者多次相同类型的事件，所有的绑定将会依次触发 
2、支持DOM事件流的 
3、进行事件绑定传参不需要on前端 
addEventListener(“click”,function(){},false);//此时的事件就是在事件冒泡阶段执行

ie9开始，ie11 edge：addEventListener

ie9以前：attachEvent/detachEvent 
1、进行事件类型传参需要带上on前缀 
2、这种方式只支持事件冒泡，不支持事件捕获 
事件绑定是指把事件注册到具体的元素之上，普通事件指的是可以用来注册的事件

## 6、IE和DOM事件流的区别

IE9以前：attachEvent(“onclick”)、detachEvent(“onclick”) 
IE9开始跟DOM事件流是一样的，都是addEventListener

比较attachEvent和addEventListener： 
1、attachEvent只支持事件冒泡 addEventListener既支持事件冒泡，也支持事件捕获 
2、参数：attachEvent事件类型需要on前缀 addEventListener事件类型不需要on前缀 
3、如果使用attachEvent对一个元素的目标阶段绑定了多次事件，那么会按照绑定顺序的相反顺序进行触发 
如果使用addEventListener对一个元素的目标阶段绑定了多次事件，那么会按照绑定顺序进行触发

## 7、IE和标准下有哪些兼容性的写法

a、获取事件对象：var ev = ev || window.event 
var ev=ev?ev:window.evnet; 
srcElement：IE9之前的浏览器用来获取事件目标元素 
target：IE9+、ff、chrome用来获取事件的目标元素 
b、获取事件目标元素：var target = ev.srcElement||ev.target 
c、innerText

## 8、call和apply的区别

考点：call和apply的用法

call和apply相同点：改变函数中this的指向

不同点：函数参数的传递形式 
call将函数参数依次传入 
apply将函数参数用一个数组的形式传入

无参数调用：

function fn(){
    alert(this.name);
}
var p1={name:1};
fn.call(p1);
fn.apply(p1);
有参数调用：

function fn2(name,age){
    this.name=name;
    this.age=age;
}
var p1={};
fn2.call(p1,"张三",20);
fn2.apply(p1,["张三",20]);

## 9、如何实现js中的继承

考点：继承的多种方式（参考 高设6.3）

1、原型继承的第一种方式：
function Cat(name){
    this.name=name;
}
//原型继承
Cat.prototype.say=function(){
    alert("你好，我是一只猫，我叫："+this.name);
}
2、原型继承第二种方式：
function Cat(name) {
    this.name = name;
}
function Animal() {}
Animal.prototype.run = function () {
    alert("动物跑");
};
Cat.prototype = new Animal();
Cat.prototype.constructor=Cat;
3、借用构造函数
function Cat(name,age) {
    Animal.call(this,name,age);
}
function Animal(name,age) {
    this.name = name;
    this.age=age;
}
4、经典继承
function create(obj) {
    if(Object.create) {
    return Object.create(obj);  
    } else {
    function F(){};
    F.prototype = obj;
    return new F();
    } 
}

## 10、JavaScript this、闭包、作用域

this：指向调用上下文

作用域：定义一个函数就开辟了一个局部作用域，整个js执行环境有一个全局作用域

闭包：一个函数可以访问其他函数中的变量（闭包是一个受保护的变量空间）

var f=(function fn(){
    var name=1;
    return function(){
        name++;
        console.log(name);
    }
})();

## 11、事件委托是什么

利用事件冒泡的原理，将事件绑定在父容器中，让父容器代为触发

## 12、闭包是什么，有什么特性，对页面有什么影响

闭包就是能够读取其他函数内部变量的函数。 
闭包的缺点： 
1 更多的内存消耗 
2 性能问题（跨作用域访问） 
3滥用闭包函数会造成内存泄露，因为闭包中引用到的包裹函数中定义的变量都永远不会被释放，所以我们应该在必要的时候，及时释放这个闭包函数

闭包是一种特殊的对象。它由两部分构成：函数，以及创建该函数的环境。 
可以把闭包简单理解成 “定义在一个函数内部的函数”，闭包就是将函数内部和函数外部连接起来的一座桥梁。闭包有如下特性： 
a. JavaScript允许你使用在当前函数以外定义的变量 
b. 即使外部函数已经返回，当前函数仍然可以引用在外部函数所定义的变量 
c. 闭包可以更新外部变量的值 
d. 用闭包模拟私有方法 
由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题

## 13、如何阻止事件冒泡和默认事件

阻止事件冒泡： 
IE9+ FF Chrome：e. stopPropagation(); 
window.event.cancelBubble=true;//ie9之前

默认行为：html标签所具有的默认行为，比如： 
a、点击a标签，就会默认跳转到指定的页面 
b、点击submit按钮，就会自动提交表单 
适用场景： 
1、异步操作 
2、提交表单之前对表单进行一些基本的验证，比如邮箱是否合法，用户名是不是满足指定的格式 
为了不让a点击之后跳转，我们就要给他的点击事件进行阻止 
3、文本框获得焦点

阻止默认行为： 
IE9之前：window.event.returnValue=false; 
IE9+ FF Chrome： e.preventDefault();

## 14、添加 删除 替换 插入到某个节点的方法

obj.appendChild() 
insertBefore 
obj.insertBefore(newElement, referenceElement ) 
参数1：被插入的元素 
参数2：目标元素

obj.replaceChild(newChild, oldChild)//替换
obj.removeChild(child)//删除
1
2
15、javascript的本地对象，内置对象和宿主对象
本地对象为Array RegExp等可以new实例化 
内置对象为global Math 等不可以实例化的 
宿主为浏览器自带的document,window 等

## 16、document load 和document ready的区别

document.onload 是在结构和样式加载完才执行js 
document.ready原生中没有这个方法，jquery中有 $().ready(function)

DOMCententLoaded事件：页面的文档结构（DOM树）加载完之后就会触发

window.onload：不仅仅要在结构和样式加载完，还要执行完所有的外部样式、图片这些资源文件，全部加载完才会触发window.onload事件

## 17、”==”和“===”的不同

==：会自动转换类型 
===：先判断左右两边的数据类型，如果数据类型不一致，直接返回false 
之后才会进行两边值的判断

1==”1”
null==undefined;//==true
1
2
18、javascript的同源策略
一段脚本只能读取来自于同一来源的窗口和文档的属性，这里的同一来源指的是主机名、协议和端口号的组合 
http,ftp:协议 
关键词解释： 
主机名：localhost、www.baidu.com 
协议：http https ftp 
端口：一个网站对应着一个端口， http协议的默认端口：80 
https协议的默认端口是8083 
同源策略带来的麻烦：ajax在不同域名下的请求无法实现， 
如果说想要请求其他来源的js文件，或者json数据，那么可以通过jsonp来解决 
跨域解决方式一 
跨域解决方式二

## 19、编写一个数组去重的方法

var arr=[1,1,3,4,2,4,7]; 
=>[1,3,4,2,7] 
思路1： 
1、先创建一个空数组，用来保存最终的结果 
2、循环数组元素，判断元素在新数组中是否有相同元素，如果没有就插入到新数组中 
3、返回新数组 
代码1：

function unique(arr){
    var result=[];
    for (var i = 0, len = arr.length; i < len; i++) {
        var arri = arr[i];
        if(result.indexOf(arri)<0){
            result.push(arri);
        }
    }
    return result;
}

## 20、JavaScript是一门什么样的语言，它有哪些特点？

弱类型、脚本语言、面向对象、 
没有标准答案。 
运行环境：JS引擎（v8(Chrome)/SpiderMonkey(FireFox)/JavaScriptCore(Safari) 
/Chakra(IE)） 
语言特性： 
1、面向对象：原型继承、构造函数、原型链 
2、动态语言：弱类型语言

//动态语言的特性
var num=10;//num是一个数字类型
num="jim";//此时num又变成一个字符串类型

//我们把一个变量用来保存不同数据类型的语言称之为一个动态语言
//静态语言：c# java c c++ OC
//int a;
//静态语言在声明一个变量就已经确定了这个变量的数据类型，
//  而且在任何时候都不可以改变他的数据类型

## 21、JavaScript的数据类型都有什么？

基本数据类型：number、string、boolean、undefined、null 
复杂数据类型：Object(Array,Date,RegExp,Function)

## 22、已知ID的Input输入框，希望获取这个输入框的输入值，怎么做？(不使用第三方框架)

document.getElementById(“ID”).value
1

## 23、希望获取到页面中所有的checkbox怎么做？(不使用第三方框架)

var domList = document.getElementsByTagName("input");
var ckList = [];//返回的所有的checkbox
var len = domList.length;
for (var i = 0; i < len; i++) {
    if (domList[i].type == "checkbox") {
        ckList.push(domList[len]);
    }
}

## 24、设置一个已知ID的DIV的html内容为xxxx，字体颜色设置为黑色(不使用第三方框架)

​    var dom = document.getElementById(“ID”);
dom.innerHTML = “xxxx”
dom.style.color = “#000”;//”black”
1
2
3

## 25、当一个DOM节点被点击时候，我们希望能够执行一个函数，应该怎么做？

HTML事件绑定：

DOM0事件绑定：xxx.onclick = test 
DOM2事件绑定：addEventListener(div1, ‘click’, test) 
扩展：Javascript的事件流模型都有什么？ 
事件流： 
从最不确定的元素(最外层容器)到目标元素，再由目标元素到最不确定的元素(最外层容器)； 
也就是说先经历事件捕获，到目标元素，再经历事件冒泡 
“事件冒泡”：事件开始由最具体的元素接受，然后逐级向上传播 
“事件捕捉”：事件由最不具体的节点先接收，然后逐级向下，一直到最具体的

## 26、看下列代码输出为何？解释原因。

​    var a;
alert(typeof a); // “undefined”
//alert(b); // 报错 
b=10;
alert(typeof b);//”number”
答案：undefined、number 
undefined产生情况： 
1、一个变量定义了却没有被赋值 
2、想要获取一个对象上不存在的属性或者方法: 
3、一个数组中没有被赋值的元素 
4、调用函数，参数未传 
扩展：not defined语法错误

## 27、看下列代码,输出什么？解释原因。

​    var a = null;
alert(typeof a); //object
1
2

## 28、看下列代码,输出什么？解释原因。

var undefined;//此时undefined这个变量的值是undefined
undefined == null; // true
1 == true;   // true
此时会把布尔类型的值转换为数字类型 true=1 false=0
2 == true;   // false
0 == false;  // true
0 == '';     // true
NaN == NaN;  // false isNaN
[] == false; // true   解释：会把[]和false都通过Number()转换为数字类型
[] == ![];   // true   解释：![]：false
[]==[];//false
一个是number一个是string时，会尝试将string转换为number 
一个是number一个是boolean，将boolean转换为number，结果：true：1 false：0 
一个是object 另一个是string或number，将Object转换成number或string 
所以，对于0、空字符串的判断，建议使用 “===” 。“===”会先判断两边的值类型，类型不匹配时为false。

## 28.2、看下列代码会有什么样的输出？

var foo = "11"+2-"1";  
console.log(foo);//112-1=111
console.log(typeof foo);//”number”
1
2
3
考点： 
1、数字和字符串都可以用加法运算符，数字和字符串相加，结果就是一个字符串 
2、但是减法运算符只能用于两个数字之间，想要执行减法运算，必须把两边数字都变成数字类型的 
答案：”111”、”number”

## 29、看代码给答案。

var a = new Object();
a.value = 1;
b = a; //b.value=1
b.value = 2;//b.value=2;a.value=2，因为a和b指向同一块引用类型的值
alert(a.value);
1
2
3
4
5
答案：2（考察引用数据类型细节）

## 30、已知数组var stringArray = [“This”, “is”, “Baidu”, “Campus”]，alert出”This is Baidu Campus”。

考点：数组的join方法的使用 
答案：alert(stringArray.join(“ ”))

## 30.2、已知有字符串foo=”get-element-by-id”,写一个function将其转化成驼峰表示法”getElementById”。

​    function combo(msg){
​    var arr=msg.split("-");//[get,element,by,id]
​    for(var i=1;i<arr.length;i++){
​        arr[i]=arr[i].[0].toUpperCase()+arr[i].substring(1);//Element
​    }
​    msg=arr.join("");//msg=” getElementById”
​    return msg;
}

## 31、var numberArray = [3,6,2,4,1,5];

1) 实现对该数组的倒排，输出[5,1,4,2,6,3]

function reverseArray(arr){
    var result=[];
    //方法1：
    /*for (var i = arr.length - 1; i >= 0; i--) {
        result.push(arr[i]);
    }*/
    //方法2：
    for (var i = 0, len = arr.length; i < len; i++) {
        result.unshift(arr[i]);
    }
    return result;
}
2) 实现对该数组的降序排列，输出[6,5,4,3,2,1] 
冒泡排序过程演示

function sortDesc(arr) {
    for (var i = 0, len = arr.length; i < len; i++) {
        for (var j = i + 1, len2 = arr.length; j < len2; j++) {
            //>就是降序 <就是升序
            if (arr[j] > arr[i]) {
                var temp = arr[j];
                arr[j] = arr[i];
                arr[i] = temp;
            }
        }
    }
    return arr;
}

## 32、输出今天的日期，以YYYY-MM-DD的方式，比如今天是2014年9月26日，则输出2014-09-26

考点：日期对象Date相关API的使用

var d = new Date();
1
// 获取年，getFullYear()返回4位的数字 
var year = d.getFullYear(); 
// 获取月，月份比较特殊，0是1月，11是12月 
var month = d.getMonth() + 1; 
// 变成两位 
month = month < 10 ? ‘0’ + month : month; 
// 获取日 
var day = d.getDate(); 
day = day < 10 ? ‘0’ + day : day; 
alert(year + ‘-’ + month + ‘-’ + day);

## 33、将字符串”{[Math Processing Error]id}</td><td>{name}</td></tr>{[Math Processing Error]id}”中的{id}替换成10，{$name}替换成Tony （使用正则表达式）

考点：正则表达式、字符串的replace方法的使用 
答案：”{[Math Processing Error]id}</td><td>{id}_{$name}”.replace(/{\$id}/g, ’10′).replace(/{\$name}/g, ‘Tony’);

## 34、为了保证页面输出安全，我们经常需要对一些特殊的字符进行转义，请写一个函数escapeHtml，将<, >, &, “进行转义

function escapeHtml(str) {
1
//[<>”&]:中括号中字符只要其中的一个出现就代表满足条件 
//给replace第二个参数传递一个回调函数，回调函数中参数就是匹配结果，如果匹配不到就是null

return str.replace(/[<>”&]/g, function(match) {
    switch (match) {
      case “<”:
         return “&lt;”;
      case “>”:
          return “&gt;”;
      case “&”:
          return “&amp;”;
      case “\””://双引号包裹一个单引号：“’” 单引号包裹一个双引号 ‘””’
         return “&quot;”;
     }
  });
}
1
2
3
4
5
6
7
8
9
10
11
12
13

## 35、foo = foo||bar ，这行代码是什么意思？为什么要这样写？

这种写法称之为短路表达式 
相当于：

var foo;
if(foo){
    foo=foo;
}else{
    foo=bar;
}
1
2
3
4
5
6
答案：常用于函数参数的空判断 
短路表达式：作为”&&”和”||”操作符的操作数表达式，这些表达式在进行求值时，只要最终的结果已经可以确定是真或假，求值过程便告终止，这称之为短路求值。 
考点：if条件的真假判定 
记住以下是false的情况：空字符串、false、undefined、null、0

## 36、看下列代码，将会输出什么?

考点：1、变量作用域 2、变量声明提升

var foo = 1;
function f(){
    console.log(foo);
    var foo = 2;
    console.log(foo);
}
f();
1
2
3
4
5
6
7
答案：输出undefined 和 2。

## 37、用js实现随机选取10–100之间的10个数字，存入一个数组，并排序。

var iArray = []; 
function getRandom(istart, iend){
        var iChoice = iend - istart +1;
        return Math.floor(Math.random() * iChoice+ istart);
}

## Math.random()就是获取0-1之间的随机数（永远获取不到1）

for(var i=0; i<10; i++){
var result= getRandom(10,100);
        iArray.push(result);
}
iArray.sort();
1
2
3
4
5
6
7
8
9
10
11

## 38、把两个数组合并，并删除第二个元素。

考点：1、数组的concat、splice用法 
splice() 方法删除数组的元素，或者向数组中添加元素，然后返回被删除的项目。 
参数1：从何处开始删除数组的元素（使用负数则从数组的末尾开始） 
参数2：要删除的元素个数（如果是0，就代表不删除） 
参数3，4，5。。。：要添加的元素

var array1 = ['a','b','c'];
1
var bArray = [‘d’,’e’,’f’]; 
var cArray = array1.concat(bArray); 
cArray.splice(1,1);

## 39、怎样添加、移除、移动、复制、创建和查找节点（使用原生JS实现）

1）创建新节点 
createDocumentFragment() //创建一个DOM文档片段 
createElement() //创建一个具体的元素 
createTextNode() //创建一个文本节点 
2）添加、移除、替换、插入 
appendChild() //追加 
removeChild() //移除 
replaceChild() //替换 
insertBefore() //插入 
3）查找 
getElementsByTagName() //通过标签名称 
getElementsByName() //通过元素的Name属性的值 
getElementsByTagName() // 通过类名查找 
getElementById() //通过元素Id，唯一性

## 40、有这样一个URL：http://item.taobao.com/item.htm?a=1&b=2&c=&d=xxx&e，请写一段JS程序提取URL中的各个GET参数(参数名和参数个数不确定)，将其按key-value形式返回到一个json结构中，如{a:’1′, b:’2′, c:”, d:’xxx’, e:undefined}。

答案：

function serlize(url){
    var result={};
    //1、寻找？后面的字符串
    url=url.substr(url.indexOf("?")+1);
    //2、将字符串用&分隔
    var args=url.split("&");//[“a=1”,”b=2”]
    for (var i = 0, len = args.length; i < len; i++) {
        var arg = args[i];
    var item = arg.split('=');
        //3、对象的键=值
        result[item[0]]= item[1];
    }
    return result;
}
serlize(‘http://item.taobao.com/item.htm?a=1&b=2&c=&d=xxx&e‘);

## 41、正则表达式构造函数var reg=new RegExp(“xxx”)与正则表达字面量var reg=//有什么不同？匹配邮箱的正则表达式？

RegExp 
答案：当使用RegExp()构造函数的时候，不仅需要转义引号（即\”表示”），并且还需要双反斜杠（即\表示一个\）。使用正则表达字面量的效率更高。 
邮箱的正则匹配： 
var regMail = /^([a-zA-Z0-9_-])+@([a-zA-Z0-9_-])+((.[a-zA-Z0-9_-]{2,3}){1,2})$/; 
41.2、.看下面代码，给出输出结果。

for(var i=1;i<=3;i++){
  setTimeout(function(){
      console.log(i);    
  },0);  
}
1
2
3
4
5
答案：4 4 4。 
考点：setTimeout的执行原理——Javascript事件处理器在线程空闲之前不会运行。 
JavaScript运行机制：事件循环 
追问，如何让上述代码输出1 2 3？ 
代码1：用立即执行函数

for(var i=1;i<=3;i++){ 
setTimeout((function(num){ 
return function(){ 
console.log(num); 
}

})(i),0);
1
} 
代码2：使用闭包 
for(var i=1;i<=3;i++){ 
setTimeout((function(){ 
var j=i; 
return function(){ 
console.log(j); 
}; 
})(),0); 
}

## 42、写一个function，清除字符串前后的空格。（兼容所有浏览器）

使用自带接口trim()，考虑兼容性(IE9以下浏览器不支持)： 
考点：1、原型扩展 2、正则表达式 3、字符串的replace方法 
if(typeof String.prototype.trim !=”function”){ 
String.prototype.trim=function(){ 
return this.replace(/^\s+|\s+$/g,”“); 
} 
} 
var str=” hello “;

## 43、Javascript中callee和caller的作用？

arguments.callee：获得当前函数的引用 
fn.caller是返回一个对函数的引用，该函数调用了当前函数；（被废弃） 
callee是返回正在被执行的function函数，也就是所指定的function对象的正文。

## 44、Javascript中, 以下哪条语句一定会产生运行错误？ 答案( BC )

A、var _变量=NaN; 
B、var 0bj = []; 
C、var obj = //; 
D、var obj = {}; 
//正确答案：BC

## 45、以下两个变量a和b，a+b的哪个结果是NaN？ 答案( C )

A、var a=undefind; b=NaN //拼写 
B、var a=‘123’; b=NaN 
C、var a =undefined , b =NaN 
D、var a=NaN , b=’undefined’ 
解析：A、拼写错误 B、结果是字符串 D、结果是字符串

## 46、var a=10; b=20; c=4; ++b+c+a++ 以下哪个结果是正确的？答案( B )

考点：++运算符的使用 21+4+10=35 
A、34 B、35 C、36 D、37 
//var a=10; b=20; c=4; 
//++b+c+a++ 
//21+4+10=35;

var a = 1; 
a++ + a++ = ？ 
a = 1; 
a++ + ++a = ? 
a = 1; 
++a + a++ = ? 
a = 1; 
++a + ++a = ?

## 47、下面的JavaScript语句中，（ D ）实现检索当前页面中的表单元素中的所有文本框，并将它们全部清空

A. for(vari=0;i< form1.elements.length;i++) {
if(form1.elements.type==”text”)
form1.elements.value=”";
}

B. for(vari=0;i<document.forms.length;i++) {
if(forms[0].elements.type==”text”)
forms[0].elements.value=”";
}
C. if(document.form.elements.type==”text”)
form.elements.value=”";
D. for(vari=0;i<document.forms.length; i++){
var form= document.forms[i];
for(var j=0;j< form.elements.length; j++){
if(form [j].type==”text”)
form.elements [j].value=”";
}
}

## 48、要将页面的状态栏中显示“已经选中该文本框”，下列JavaScript语句正确的是（ A ）

A. window.status=”已经选中该文本框” 
B. document.status=”已经选中该文本框” 
C. window.screen=”已经选中该文本框” 
D. document.screen=”已经选中该文本框”

## 49、以下哪条语句会产生运行错误：（A、D）

A.var obj = (); 
B.var obj = []; 
C.var obj = {}; 
D.var obj = //;

## 50、以下哪个单词不属于javascript保留字：（B）

A.with 
B.parent 
C.class 
D.void

## 51、请选择结果为真的表达式：（C）

考点：1、instanceof：用于检测某个对象是不是某个构造函数的实例 
2、==、===用于数据类型的判断 
A.null instanceof Object 
B.null === undefined 
C.null == undefined 
D.NaN == NaN

## 52、Javascript中, 如果已知HTML页面中的某标签对象的id=”username”，用_document.ge2tElementById(‘username’) _方法获得该标签对象。

## 53、typeof运算符返回值中有一个跟javascript数据类型不一致，它是”function”。

考点：type运算符

## 54、定义了一个变量，但没有为该变量赋值，如果alert该变量，javascript弹出的对话框中显示undefined___ 。

55、分析代码，得出正确的结果。
var a=10, b=20 , c=30; 
++a; 
a++; 
e=++a+(++b)+(c++)+a++;//13+21+30+13 
alert(e); 
弹出提示对话框：77 
var a=10, b=20 , c=30; 
++a;//a=11 
a++;//a=11 
e=++a+(++b)+(c++)+a++; 
//a=12 13+21+30+13=77 
alert(e);

## 56、写出函数DateDemo的返回结果，系统时间假定为今天

function DateDemo(){ 
var d, s=”今天日期是：”; 
d = new Date(); 
s += d.getMonth() + “/”; 
s += d.getDate() + “/”; 
s += d.getFullYear(); 
return s;} 
考点：Date对象的api使用， 
注意点：getMonth()打印的是比当前月份小1的数字 
结果：今天日期是：

## 57、写出程序运行的结果？

for(var i=0, j=0; i<10, j<6; i++, j++){ 
//循环结束条件：j=5 i=5 
k = i + j;//k=10 
} 
//结果：10 
for循环 
解析：最终的结果其实就是程序运行的最后一个表达式的值 
这里考的是逗号运算符的特性；

## 58、阅读以下代码，请分析出结果：

var arr = new Array(1 ,3 ,5);
arr[4]='z';         //arr=[1,3,5,undefined,’z’]
arr2 = arr.reverse();   //arr2=[’z’,undefined,5,3,1];
                    //arr=[’z’,undefined,5,3,1]
arr3 = arr.concat(arr2);
alert(arr3);
1
2
3
4
5
6
考点：reverse 方法颠倒数组中元素的位置，并返回该数组的引用。 
答案：弹出：z,,5,3,1,z,,5,3,1

## 59、补充按钮事件的函数，确认用户是否退出当前页面，确认之后关闭窗口；

考点：confirm的用法 
function closeWin(){ //在此处添加代码 if(confirm("确定要退出吗？")){ window.close(); } }



## 60、写出简单描述html标签（不带属性的开始标签和结束标签）的正则表达式，并将以下字符串中的html标签去除掉

考点：正则表达式以及replace()的使用 
var str = “

这里是div
里面的段落

”; 
//
<scripttype=”text/javascript”>
var reg = /<\/?\w+\/?>/gi;//img br hr
x?  匹配问号前面的内容出现0 或 1 次。
1
2
3
var str = “

这里是div
里面的段落

”; 
alert(str.replace(reg,””)); 

## 61、完成foo()函数的内容，要求能够弹出对话框提示当前选中的是第几个单选框。

<html>

<head>
<metahttp-equiv=”Content-Type” content=”text/html;charset=utf-8″ />
</head>
<body>
<script type=”text/javascript” >
function foo() {
//在此处添加代码
var rdo =document.form1.radioGroup;//表单下面的所有的单选框
for(var i =0 ;i<rdo.length;i++){
if(rdo[i].checked){
alert(“您选择的是第”+(i+1)+”个单选框”);
} 
}
}

document.getElementsByTagName(“input”)[4].onclick = function(e) {
e.preventDefault();
foo();
};

</script>
<body>
<form name=”form1″ >
<input type=”radio” name=”radioGroup” />
<input type=”radio” name=”radioGroup”/>
<input type=”radio” name=”radioGroup”/>
<input type=”radio” name=”radioGroup”/>
<input type=”submit”/>
</form>
</body>
</html>
32

## 62、完成函数showImg()，要求能够动态根据下拉列表的选项变化，更新图片的显示

考点：1、下拉框切换：onchange事件 2、通过value获取下拉框的值

function showImg (oSel) { //在此处添加代码 var str = oSel.value; document.getElementById(“pic”).src= str+”.jpg”; }




城市生活 
都市早报 
青山绿水 
63、截取字符串abcdefg的efg
alert(‘abcdefg’.substring(4));

## 64、列举浏览器对象模型BOM里常用的至少4个对象，并列举window对象的常用方法至少5个

对象：window document location screen history navigator 
方法：alert() confirm() prompt() open() close()

## 65、简述列举文档对象模型DOM里document的常用的查找访问节点的方法并做简单说明

document.getElementById 根据元素id查找元素 
document.getElementsByName 根据元素name查找元素 
document.getElementsByTagName 根据指定的元素名查找元素

66、希望获取到页面中所有的checkbox怎么做？(不使用第三方框架)

var domList = document.getElementsByTagName(‘input’)
var checkBoxList = [];
var len = domList.length;　　//缓存到局部变量
while (len--) {
　　if (domList[len].type == ‘checkbox’) {
    　　checkBoxList.push(domList[len]);
　　}
}
68、javascript中有哪几种数据类型，分别写出中文和英文。
string boolean number null undefined object 
字符串 布尔 数值 空值 未定义 对象

## 69、javascript中==和===的区别是什么？

举例说明。
==会自动进行类型转换，比如：1==”1”，数字和字符串比较，会将非数字转变为数字 
===不会，比如：1===”1”由于两边数据类型不一致，所以结果必然是false

## 70、简述创建函数的几种方式

第一种（函数声明）：

function sum1(num1,num2){
   return num1+num2;
}
1
2
3
第二种（函数表达式）：

var sum2 = function(num1,num2){
   return num1+num2;
}
1
2
3
匿名函数：没有函数名称，无法通过函数名称调用

function(){}:只能自己执行自己
1
第三种（Function构造函数方式）：

var sum3 = new Function("num1","num2","return num1+num2");
1

## 71、Javascript如何实现继承？

原型链继承，借用构造函数继承，组合继承，寄生式继承，寄生组合继承

## 72、Javascript创建对象的几种方式？

构造函数方式，原型模式，混合构造函数原型模式，工厂方式，动态原型方式 
混合构造函数+原型模式：

function Robot(name){
    this.name=name;
}
Robot.prototype.say=function(){
    alert("大家好，我叫"+this.name);
};
var alphaGo=new Robot("阿尔法狗");
alphaGo.say();
工厂方式：

function create(name,age){
    var o={};
    o.name=name;
    o.age=age;
    return o;
}
var p1=create("张三",20);
动态原型方式：

function Person(name,work){
    this.name=name;
    if(work){
        Person.prototype.doWork=function(){
            alert("我正在从事"+work+"的工作");
        }
    }
}
var p1=new Person("姚明");
var p2=new Person("喵喵","程序猿鼓励师");

## 73、把 Script 标签 放在页面的最底部的body封闭之前 和封闭之后有什么区别？浏览器会如何解析它们？

如果说放在body的封闭之前，将会阻塞其他资源的加载 
如果放在body封闭之后，不会影响body内元素的加载

## 74、iframe的优缺点？

优点： 

1. 解决加载缓慢的第三方内容如图标和广告等的加载问题 
2、并行加载脚本 
缺点： 
1、iframe会阻塞主页面的onload事件 
2、即时内容为空，加载也需要时间，因为需要http请求 
3、不便于SEO 
4、内外网页维护麻烦

## 75、请你谈谈Cookie的弊端？

什么是Cookie？Cookie是指某些网站为了辨别用户身份或进行session跟踪而储存在用户本地浏览器终端上的数据。一般来说，Cookie通过HTTP Headers从服务器端返回到浏览器上。首先，服务器端在响应中利用Set-Cookie header来创建一个Cookie ，然后，浏览器在它的请求中通过Cookie header包含这个已经创建的Cookie，并且把它返回至服务器，从而完成浏览器的验证。

Cookie的保存形式 
IE 浏览器将站点的 Cookie 保存在文件名格式为 @.txt 的文件中，其中 是您的帐户名。例如，如果您的名称为 user，您访问的站点为 www.codetc.com，那么该站点的 Cookie 将保存在名为 user@codetc.com.txt 的文件中。（该文件名可能包含一个顺序的编号，如 user@codetc.com [1].txt。） Cookie 文本文件是与用户相关的，所以会按照帐户分别保存。

Cookie的限制 
一个 Cookie 大约占用 50 个字符的基本空间开销（用于保存有效期信息等），再加上其中保存的值的长度，其总和接近 4K 的限制。大多数浏览器只允许每个站点保存 20 个 Cookie。

为什么选择把信息保存到cookie中 
由于session在使用过程中会造成极大的网络负担，随之带来的就是性能问题，所认我们可以把session以Cookie的形式保存在客户端。当然有时候也是为了完成某些特定的功能而使用cookie，比如实现记住密码和自动登录。

优点：是极高的扩展性和可用性 
通过良好的编程，控制保存在cookie中的session对象的大小。 
通过加密和安全传输技术（SSL），减少cookie被破解的可能性。 
只在cookie中存放不敏感数据，即使被盗也不会有重大损失。 
控制cookie的生命期，使之不会永远有效。偷盗者很可能拿到一个过期的cookie。

缺点：数量限制和安全问题 
Cookie是有数量和长度限制的。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。 
安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。 
有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。

缺点： 
1.Cookie数量和长度的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。 
2.安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。 
3.有些状态不可能保存在客户端。例如， 
一、为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。 
二、比如用户密码输入错误超过3次，我们应该在后端数据库中保存错误数据

## 76、DOM操作——怎样添加、移除、移动、复制、创建和查找节点。

创建新节点 
createDocumentFragment() // 创建一个DOM片段 
createElement() // 创建一个具体的元素 
createTextNode() // 创建一个文本节点
添加、移除、替换、插入 
appendChild() 
removeChild() 
replaceChild() 
insertBefore() // 在已有的子节点前插入一个新的子节点
查找 
getElementsByTagName() // 通过标签名称 
getElementsByName() // 通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的) 
getElementById() // 通过元素Id，唯一性

## 77、js延迟加载的方式有哪些？

defer和async 
defer：当文档加载完成之后执行 
async：异步执行脚本
动态创建DOM方式 
创建script，插入到DOM中，加载完毕后callBack）

## 78、documen.write和 innerHTML 的区别？

document.write 指定位置输出 
dom.innerHTML 可以重绘指定元素的内容 
document.write和innerHTML的区别

## 79、哪些操作会造成内存泄漏？

内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。 
垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为 0（没有其他对象引用过该对象），或对该对象的惟一引用是循环的，那么该对象的内存即可回收。 

1. setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。 
2. 闭包 
3. 控制台日志 
内存泄漏的几种情况

## 81、split() join() 的区别

答：前者是切割成数组的形式，后者是将数组转换成字符串

## 82、数组方法pop() push() unshift() shift()各表示什么意思？

答：push()尾部添加、pop()尾部删除、Unshift()头部添加、shift()头部删除

## 83、判断一个字符串中出现次数最多的字符，统计这个次数

答：var str = ‘asdfssaaasasasasaa’;

var json = {};
for (var i = 0; i < str.length; i++) {
        if(!json[str.charAt(i)]){
                json[str.charAt(i)] = 1;// json[str[i]] = 1;
        }else{
                json[str.charAt(i)]++;
        }
};
var iMax = 0;
var iIndex = '';
for(var i in json){
        if(json[i]>iMax){
                iMax = json[i];
                iIndex = i;
        }
}
alert(‘出现次数最多的是:’+iIndex+’出现’+iMax+’次’);

## 84、javascript的typeof返回哪些数据类型

Object number function boolean underfind

## 85、例举3种强制类型转换和2种隐式类型转换?

强制（parseInt,parseFloat,number） 
隐式（== – ===）

## 86、split() join() 的区别

前者是切割成数组的形式，后者是将数组转换成字符串

## 87、数组方法pop() push() unshift() shift()

push()尾部添加 shift() 尾部删除 
unshift() 头部添加 shift() 头部删除

## 93、写一个获取非行间样式的函数

dom.style.color;//行内的color属性的值
function getStyle(obj,attr)
{
        if(obj.currentStyle)    //ie9之前
        {
            return obj.currentStyle[attr];
        }
        else{               //ie9+ 标准浏览器
            window.getComputedStyle(obj,null)[attr];
        }
}

## 95、闭包是什么，有什么特性，对页面有什么影响

闭包就是能够读取其他函数内部变量的函数。 
闭包 此链接可查看（问这个问题的不是一个公司）

## 96、解释jsonp的原理，以及为什么不是真正的ajax

动态创建script标签，回调函数 
Ajax是页面无刷新请求数据操作

## 99、字符串反转，如将 ‘12345678’ 变成 ‘87654321’

//大牛做法；
1
//思路：先将字符串转换为数组 split()，利用数组的反序函数 reverse()颠倒数组，再利用 join() 转换为字符串 
var str = ‘12345678’; 
str = str.split(”).reverse().join(”);

Ajax 
Ajax交互 
阿里-面试题

100、将数字 12345678 转化成 RMB形式 如： 12,345,678
//个人方法；
1
//思路：先将数字转为字符， str= str + ” ; 
//利用反转函数，每三位字符加一个 ‘,’最后一位不加； re()是自定义的反转函数，最后再反转回去！

for(var i = 1; i <= re(str).length; i++){
    tmp += re(str)[i - 1];
    if(i % 3 == 0 && i != re(str).length){
        tmp += ',';
    }

