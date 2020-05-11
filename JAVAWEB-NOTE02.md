[TOC]

unit04-JavaScript
================

JavaScript简介
--------------

### 什么是JavaScript(了解)

全称叫做JavaScript，简称叫做JS

由NetScape(网景)公司提供，是一门专门嵌入在浏览器中执行的脚本语言

JS运行在浏览器中，负责实现网页中的动画效果

或者是实现表单校验等功能

### JS特点和优势(了解)

**1、特点：**

(1)JS是一门直译式的语言(边解释边执行，没有编译的过程)

(2)JS是一门基于对象的语言(JS中没有类的概念,也没有编译的过程)

JS中是有对象的(内置对象、自定义对象)

(3)JS是一门弱类型的语言(Java:强类型)

```javascript
在java中:
String s = "abc";
int n = 100;
在JS中:
var s = 100;
s = "abc";
s = true;
s = [];
s = function(){}
```

**2、优势：**

(1)JS具有良好的交互性

(2)JS具有一定的安全性(只能在浏览器内部运行,不能访问浏览器以外的资源)

(3)JS具有跨平台性(JS 浏览器)

( JS语言是跨平台的，是因为有浏览器，但浏览器不跨平台

Java语言是跨平台的，是因为有虚拟机，但虚拟主机不跨平台 )

### 在HTML书写JS的方式

**1、在script标签内部可以书写JS代码：**

在head或者body标签内部可以添加一个script标签，在script标签内部可以直接书写JS代码！

```html
<!-- 在script标签内部可以书写JS注释和JS代码 -->
<script type="text/javascript">
  //JS的单行注释
  /* JS的多行注释 */
	alert( "在html中引入JS的第一种方式..." );
</script>
```

**2、通过script标签引入外部的JS文件**

在head或body标签内部，可以通过script标签引入外部的JS文件。例如：

```html
<!-- 通过script标签可以引入外部的JS文件 -->
<script src="demo.js"></script>
```
注意：(1)在引入js文件的script标签内部不要书写JS代码,例如:
```html
<script src="demo.js">
	alert( 111 ); //这里的代码不会执行
</script>
```
(2)不要将引入JS文件的script标签自闭，因为可能会导致文件引入失败，如下：
```html
<script src="demo.js" />
```
**扩展内容：也可以直接在元素上书写JS代码**

```html
<!-- 直接在元素上书写JS代码：
onclick属性用于给当前元素绑定点击事件：点击元素就会触发事件，执行相应函数
-->
<input type="button" value="点我~" onclick="alert('叫你点你还真敢点啊!!!')"/>
<input type="button" value="别点我"  onclick="console.log( new Date() )"/>
```

JavaScript语法
--------------

### 注释格式

JS的注释符号和Java的注释符号相同，如下：

```javascript
// 单行注释内容
/* 多行注释内容 */
```

### 数据类型

**1、基本数据类型**

**(1)数值类型(number)**

在JS中，所有的数值在底层都是浮点型，但是在处理和显示的过程中会自动的和整型进行转换。

```
例如：2.4+3.6=6
特殊值：Infinity(无穷大) / -Infinity(负无穷大) / NaN(非数字)
```

**(2)字符串类型(string)**

在JS中，字符串类型属于基本数据类型，字符串常量可以使用单引号或者使用双引号引起来。例如：

```javascript
var s1 = "Hello JS";
var s2 = 'Hello JS';
```

另外，JS中字符串类型有对应的包装对象（String），在需要时会自动的和包装对象进行转换。

```javascript
var s1 = "Hello JS";
console.log( typeof s1 ); //string
var s2 = new String("Hello JS");
console.log( typeof s2 ); //object
//不管是基本数据类型s1, 还是对象类型s2, 都可以当作对象来用
console.log( s1.valueOf() ); //s1是基本数据类型, 会转成对象, 调用valueOf函数
console.log( s2.valueOf() );
```

**(3)布尔类型(boolean)**

布尔类型的值有两个，分别为true和false。

(4)undefined

undefined类型的值只有一个，就是undefined，表示变量未定义(但不是指对象没有声明)。

是指声明了变量，但没有为变量赋值，该变量的值就是undefined。

```javascript
/* 1.undefined类型 */
var x;
alert( x ); //undefined
alert( y ); //抛异常
```

(5)null

null类型的值也只有一个，就是null，表示空值。

可以作为函数的返回值，表示函数返回的是一个空的对象。

注意：null和undefined类型的变量是不能调用函数或属性的，会抛异常！

**2、复杂数据类型**

主要指对象(JS的内置对象、自定义的对象、函数、数组)

### 变量声明

JS中是通过var关键字声明变量，声明的变量是不区分类型，可以指向任意的数据。例如：

```javascript
var x = 100;
x = "abc";
x = true;
x = [];
x = function(){}
x = new Object();
x = {};
```

另外，JS中多次声明同名的变量不会出现语法错误，例如：

```javascript
/* 2.变量的定义 */
var s = "Hello"; // var s; s="Hello";
var s = 123; // var s; s=123; 第二次声明变量x没有生效
alert( s ); //123
```



### JS运算符

JS和Java中的运算符大致相同，例如：

```
算术运算符: +，-，*，/，%，++，--
赋值运算符: =，+=，-=，*=，/=，%=
比较运算符: ==，!=，>，>=，<，<=
位运算符: & ， |
逻辑运算符: && ，||
前置逻辑运算符: ! (not)
三元运算符: 表达式 ? 表达式 : 表达式
。。。
```

### JS语句

JS中的语句和Java中的语句也大致相同

**1、if分支结构**

if分支结构用于基于不同的条件来执行不同的动作。语法结构如下：

```javascript
if (条件 1){
	当条件 1 为 true 时执行的代码
}else if (条件 2){
	当条件 2 为 true 时执行的代码
}else{
	当条件 1 和 条件 2 都不为 true 时执行的代码
}
```

**2、switch语句**

使用 switch 语句来选择要执行的多个代码块之一。语法结构如下：

```javascript
switch(n){
	case 1:
		执行代码块 1
		break;
	case 2:
        执行代码块 2
		break;
    ...
	default:
		与 case 1 和 case 2 不同时执行的代码
}
```

执行原理：首先设置表达式 n（通常是一个变量）。随后表达式的值会与结构中的每个case 的值做比较。如果存在匹配，则与该 case 关联的代码块会被执行。请使用 break来阻止代码自动地向下一个 case 运行。

**3、for循环语句** -- 循环代码块一定的次数

for 循环的语法结构如下：

```javascript
for (语句 1; 语句 2; 语句 3){
	被执行的代码块
}
```

**4、while循环** -- 在指定条件为真时循环执行代码块

JS中while循环也分为while和do/while循环，下面为while循环语法结构:

```javascript
while (条件){
	需要执行的代码
}
```

while 循环会在指定条件为真时循环执行代码块。

`案例1：if分支案例: 接收用户输入的成绩，判断成绩所属的等级`

```
80~100(包括80，也包括100) 优秀
60~80(包括60，但不包括80) 中等
0~60(包括0，但不包括60) 不及格
```

其他值 输入有误

代码实现如下：

```javascript
var score = prompt("请输入您的成绩: ");
if( score >= 80 && score <=100 ){
	alert("您的成绩属于: 优秀!");
}else if( score >= 60 && score < 80 ){
	alert("您的成绩属于: 中等!");
}else if( score >= 0 && score < 60 ){
	alert("您的成绩属于: 不及格!");
}else{
	alert("您的输入有误, 请重新输入!");
}
```

案例2：switch语句案例—实现一个简易的计算器：

可以接收用户输入的两个数值和一个操作符(+、-、*、/)，根据操作符号的不同，对两个数值执行不同的运算。

代码实现如下：

```javascript
//1.接收用户输入的数值和运算符, 中间用空格分隔

var str = prompt("请输入数值1、运算符、数值2，中间用空格分隔："); //"10 + 5"

//2.对用户输入的内容进行切割(以空格作为分隔符切割)

var arr = str.split(" "); // ["10", "+", "5"]

var num1 = arr[0] - 0 ;
var opt = arr[1];
var num2 = arr[2] - 0 ;
//3.通过switch分支实现计算器
switch( opt ){
	case "+":
		alert( "两个数的和为: "+( num1+num2 ) );
		break;
	case "-":
		alert( "两个数的差为: "+( num1-num2 ) );
		break;
	case "*":
		alert( "两个数的乘积为: "+( num1*num2 ) );
		break;
	case "/":
		alert( "两个数的商为: "+( num1/num2 ) );
		break;
	default:
		alert( "您输入的运算符有误, 请重新输入!" );
}
```

案例3：for循环语句案例

遍历1\~100之间的所有整数，求1\~100之间所有整数的和，并输出到控制台;

代码实现如下：

```javascript
//--------------------------------------
var i = 1;
var sum = 0;
while( i <= 100 ){
    sum += i;
    i++;
}
alert( "1~100之间所有整数的和为: "+sum );
//--------------------------------------
var sum = 0;
for( var i=0; i<=100; i++){
	sum += i;
}
alert( "1~100之间所有整数的和为: "+sum );
//--------------------------------------
```

案例4：while循环语句案例

遍历下面数组中的元素，将元素输出到控制台。

```
var arr = [123, "abc", false, new Object() ];
```

代码实现如下：

```javascript
var arr = [123, "abc", false, new Object() ];
var index = 0;
while( index < arr.length ){
	console.log( arr[index] );
	index++;
}
for( var i=0; i<arr.length; i++ ){
	console.log( arr[i] );
}
```

### JS数组

Array 对象用于在单个的变量中存储多个值。

**JS数组的声明方式一:**

```javascript
//声明一个空数组,长度为零
var arr1 = [];
//声明一个数组，并为数组设置初始值
var arr2 = ["Hello", 111, false, new Object() ];
```

**JS数组的声明方式二:**

```javascript
//声明一个空数组，长度为零
var arr3 = new Array();
//声明一个数组，并为数组设置初始值
var arr4 = new Array("Hello", 111, false, new Object());
```

**数组中的细节问题:**

(1)JS中的数组可以存储任意类型的数据

(2)JS中的数组长度是可以被任意改变的

```javascript
var arr1 = [];
console.log("此处数组的长度为: "+arr1.length ); // 0
arr1.length = 5;
console.log("此处数组的长度为: "+arr1.length ); // 5
arr1[9] = "a";
console.log("此处数组的长度为: "+arr1.length ); // 10
arr1[99] = "b";
console.log("此处数组的长度为: "+arr1.length ); // 100
```

### JS函数

函数就是一个具有功能的代码块, 可以反复调用

函数就是包裹在花括号中的代码块，前面使用了关键词 function。

**JS中声明函数的方式为:**

```
function 函数名称([参数列表]){
	函数体
}
```

或者：

```
var 变量名/函数名 = function([参数列表]){
	函数体
}
```

调用函数: 函数名称([参数列表]);

### 综合练习

(自己完成)声明一个函数fn，在函数中实现：遍历指定的两个数值(例如1和100)之间的整数，将是3的倍数的数值存入到一个数组中，并将数组返回。

1、声明fn函数

```javascript
function fn(x,y){
    var arr = [];
    for(var i=x,j=0;i<y;i++){
        if(i%3==0){
        	arr[j] = i;
        	j++;
    	}
    }
    return arr;
}
```

2、调用fn函数, 获取1\~100之间是3的倍数的数值组成的数组

var arr = fn(1,100);

3、遍历数组中的元素, 输出在网页上(提示: document.write("输出的内容") )

```javascript
for(var i=0;i<arr.length;i++){
	document.write(arr[i]+" ");
}
```

DOM操作
-------

DOM: Document Object Model，文档对象模型，其实就是JS专门为访问html元素提供的一套API。

### 案例：电灯开关

点击电灯可以实现开/关灯，代码实现如下：

```javascript
var flag = "off"; //flag表示灯的状态, off表示灯是关闭的!
function changeImg( ){
    //1.通过id获取img元素(返回是一个JS对象)
    var imgObj = document.getElementById("img1");
    if( flag == "off" ){ // 表明灯是关闭状态, 点击后则需要打开
    	imgObj.src = "imgs/on.gif";
    	flag = "on"; // 更新灯的状态为开灯
    }else{ // flag="on" 表名灯是打开状态, 点击后则需要关闭
    	imgObj.src = "imgs/off.gif";
    	flag = "off";
    }
}
```



### 案例：增删改元素

点击网页中的按钮对html元素进行操作

练习1、添加元素:添加一个div元素到body中

```javascript
function addNode(){
    //1.创建一个新的div元素(返回的是一个JS对象, 表示新创建的div元素)
    var newDivObj = document.createElement("div"); // \<div\>\</div\>
    newDivObj.innerHTML = "我是新来的....";
    //2.获取body元素(body是父元素)
    var bodyObj = document.body;
    //3.通过父元素(body)添加子元素(newDivObj)
    bodyObj.appendChild( newDivObj );
}
```

练习2、删除元素: 删除id为div_2的元素

```javascript
function deleteNode(){
    //1.获取要删除的元素(id为div_2)
    var div2 = document.getElementById("div_2");
    //2.获取id为div_2的元素的父元素
    var parent = div2.parentNode;
    //3.通过父元素删除子元素
    parent.removeChild( div2 );
}
```

练习3、更新元素内容：将div_3的内容更新为当前时间

```javascript
function updateNode(){
    //1.获取id为div_3的元素
    var div3 = document.getElementById("div_3");
    //2.获取表示当前时间的字符串
    var dateStr = new Date().toLocaleString();
    //3.将div_3元素的内容更新为当前时间
    div_3.innerHTML = dateStr;
}
```

### 案例：网页换肤

```javascript
/** 练习1：执行下面的函数，切换字体大小 */
function resize( selector ){
	//获取id为newstext元素
	var div = document.getElementById("newstext");
	//将id为newstext元素的class属性值设置为 selector
	div.className = selector;
}

/** 练习2：执行下面的函数，为页面切换不同的皮肤
	点击换肤链接时,执行changeStyle函数，将link标签的href属性值指向
	不同的css文件的路径，就会使用不同的css文件中的样式 */
//定义数组，存放不同的皮肤（css文件的路径）
var styleArr = ["css/red.css", "css/green.css", "css/blue.css"];
var index = 0;
function changeStyle(){
	//获取head中的link标签(id=link)
	var link = document.getElementById("link");
	//	将link标签的href属性值指向css文件的路径
	link.href = styleArr[index];
	index++;
	if( index == styleArr.length ){ //如果下标等于数组长度
		index = 0; //则将下标重置为0
	}
}
```



### 总结：JS获取元素

`document.getElementById( id值 )` -- 通过元素的id值，获取一个元素。返回的是表示该元素的js对象。

`document.getElementsByTagName( 元素名 )` -- 通过元素名称获取当前文档中的所有指定名称的元素，返回的是一个数组，其中包含了所有指定名称的元素。

`document.body` -- 获取当前文档中的body元素

`ele.parentNode` -- 获取当前元素的父元素。ele表示当前元素

### 总结：JS增删改元素

`document.createElement( 元素名称 )` -- 根据元素名称创建指定名称的元素，返回的是表示新创建元素的js对象

`parent.appendChild( child )` -- 通过父元素添加子元素，其中parent表示父元素，child表示子元素

`parent.removeChild( child ) `-- 通过父元素删除子元素，其中parent表示父元素，child表示子元素

`ele.innerHTML` -- 获取当前元素的html内容(从开始标签到结束标签之间的所有内容)，还可以设置当前元素的html内容(如果元素内部有内容，将会覆盖原有内容)

## htmlcss+JS作业

`03-24作业：`

1、独立完成京淘注册页面（1~2遍）

2、（选作）完成京淘的登录页面

3、完成课上讲过的JS语句案例里

```
(1) if分支结构案例: 接收用户输入的成绩, 判断成绩所属的等级
(2) switch语句: 实现一个简易计算器
(3) 综合案例
```

`03-25作业：`

完成课上讲过的DOM操作相关的案例：

```
（1）电灯开关
（2）增删改元素
（3）网页换皮肤
```

unit05-jQuery
============

jQuery简介
---------

### 什么是jQuery(了解)

jQuery: JavaScript Query  JS查询

jQuery是一门轻量的、免费开源的JS函数库（就是JS的简单框架）

jQuery可以极大的简化JS代码

jQuery的核心思想：“写的更少，但做的更多”



*轻量的：是指一个技术对代码或程序的侵入程度是比较低的。*

*或者说代码对该技术依赖程度越低，这个技术越轻。对该技术的依赖程度越高，这个技术越重。*

*jQuery本质就是一个包含了很多函数的JS文件，如果要在某一个HTML中使用这个JS文件中的函数，就必须得将JS文件引入到HTML中*



### jQuery的优势(了解)

(1) 可以极大的简化JS代码

(2) 可以像CSS选择器一样获取html元素

css中获取所有的div,给div添加样式:

```
div{ css属性... }
```

jQuery中获取所有div,给div添加边框样式:

```
$("div").css("border", "2px solid red");
```

```
JS获取id为div1的元素: document.getElementById("div1")
jQuery获取id为div1的元素: $("#div1")
```

(3) 可以通过修改css属性控制页面的效果

(4) 可以兼容常用的浏览器

比如: JS中的innerText属性、removeNode()函数、replaceNode( )函数 这些函数在某些浏览器中是无法使用的。

jQuery中提供了相应的函数（ text函数、remove函数、replaceWith函数 ）

常用浏览器：谷歌浏览器、火狐浏览器、苹果浏览器、欧朋浏览器等



### jQuery引入

jQuery的函数库文件就是一个普通的JS文件，引入jQuery和引入JS文件的方式一样。

```javascript
<!-- 在使用jQuery之前，必须先引入jQuery的函数库文件 -->
<script src="js/jquery-1.8.3.js"></script>
```

在引入jQuery函数库文件时，如果文件引入路径错误，则会导致文件引入失败，如下图：

![image-20200217103533313](JAVAWEB-NOTE02.assets/image-20200217103533313.png)



### 文档就绪事件函数

```html
<head>
<meta charset="UTF-8">
<!-- 在使用jQuery之前，必须先引入jQuery的函数库文件 -->
<script src="js/jquery-1.8.3.js"></script>
<script>
	//1.获取id为demo的h1元素
	var h1 = document.getElementById( "demo" );
	//2.获取h1元素中的内容( innerHTML )
	alert( h1.innerHTML );
</script>
</head>
<body>
	<h1 id="demo">jQuery的引入示例...</h1>
</body>
```

问题描述：上面的代码在执行时，会报一个错误：

![image-20200217105525351](JAVAWEB-NOTE02.assets/image-20200217105525351.png)

原因描述：在执行获取id为demo的元素时, h1元素还没有被浏览器加载到，所以获取不到h1元素。

**解决方式一：**

将script标签移到body内部，也就是h1元素的后面

这样浏览器在加载时，会先加载h1元素，再执行获取h1元素的代码，由于在获取h1元素之前，h1元素已经被浏览器加载过了，所以后面再获取就能够获取到！

代码示例：

```html
<body>
	<h1 id="demo">jQuery的引入示例...</h1>
	<script>
		//1.获取id为demo的h1元素
		var h1 = document.getElementById( "demo" );
		//2.获取h1元素中的内容( innerHTML )
		alert( h1.innerHTML );
	</script>
</body>
```



**解决方式二：**

将获取元素的代码放在文档就绪事件函数中，文档就绪事件函数会在浏览器加载完所有的html元素后（也就是加载完最后一个html元素时）会立即执行。

由于整个html网页都被加载了，h1元素肯定也被加载了，此时再获取h1元素就一定能获取到。

```html
<head>
<meta charset="UTF-8">
<!-- 在使用jQuery之前，必须先引入jQuery的函数库文件 -->
<script src="js/jquery-1.8.3.js"></script>
<script>
	$(function(){
		//1.获取id为demo的h1元素
		var h1 = document.getElementById( "demo" );
		//2.获取h1元素中的内容( innerHTML )
		alert( h1.innerHTML );
	});
</script>
</head>
<body>
	<h1 id="demo">jQuery的引入示例...</h1>
</body>
```

**解决方式三：**

将获取元素的代码放在一个自定义的函数中，并将该函数绑定在h1元素的点击事件上，当我们点击h1元素时会执行自定义的函数，函数执行时才获取h1元素，此时就能够获取到h1元素。

```html
<head>
<meta charset="UTF-8">
<!-- 在使用jQuery之前，必须先引入jQuery的函数库文件 -->
<script src="js/jquery-1.8.3.js"></script>
<script>
	function fn1(){
		//1.获取id为demo的h1元素
		var h1 = document.getElementById( "demo" );
		//2.获取h1元素中的内容( innerHTML )
		alert( h1.innerHTML );
	}
</script>
</head>
<body>
	<h1 id="demo" onclick="fn1()">jQuery的引入示例...</h1>
</body>
```

**总结：什么时候该使用文档就绪事件函数?**

如果在获取元素时，获取元素的代码执行的时机，比元素本身加载的时间还要早，如果元素还没有加载就获取，必然是获取不到的。

可以将获取元素的代码放在文档就绪事件函数中，等浏览器加载完整个网页后，文档就绪事件函数才会执行，此时所有的元素都被加载了，再获取任何元素都能获取到！

jQuery提供的文档就绪事件函数（简写形式）：

```html
<script>
	$(function(){
		//在浏览器加载完整个html网页后立即执行
  });
</script>
```

其完整写法为：

```html
<script>
	$(document).ready(function(){
		//在浏览器加载完整个html网页后立即执行
	})
</script>
```

JS也为我们提供了文档就绪事件函数，其写法为：

```html
<script>
	window.onload = function(){
		//在浏览器加载完整个html网页后立即执行
	}
</script>
```

jQuery选择器(重点掌握)
----------------------

### 基本选择器

```javascript
(1)元素名选择器
$("div") -- 选中所有的div元素
$("span") -- 选中所有的span元素

(2)class/类选择器
$(".s1") -- 选中所有class值为s1的元素(class值为s1的元素可能是任何元素)
$("span.s1") -- 选中所有class值为s1的span元素

(3)id选择器
$("#one") -- 选中id为one的元素

(4)多元素选择器
$("div,span,.s1,#one") -- 选中所有的div元素,以及所有的span元素,以及所有class值为s1的元素,以及id为one的元素
```

### 层级选择器

```javascript
$("div span") -- 选中所有div内部的所有span元素
$("#one span") -- 选中id为one的元素内部的所有span元素

$("#two+span") -- 选中id为two的元素后面紧邻的span兄弟元素
$("#two").next("span") -- 选中id为two的元素后面紧邻的span兄弟元素
$("#two").prev("span") -- 选中id为two的元素前面紧邻的span兄弟元素

$("#two~span") -- 选中id为two的元素后面所有的span兄弟元素
$("#two").nextAll("span") -- 选中id为two的元素后面所有的span兄弟元素
$("#two").prevAll("span") -- 选中id为two的元素前面所有的span兄弟元素

$("#two").siblings("span") -- 选中id为two的元素前、后所有的span兄弟元素
```



### 基本过滤选择器

```javascript
(1) 选中第一个div元素
$("div:first")
$("div:eq(0)")
$("div").eq(0)

(2) 选中最后一个div元素
$("div:last")
$("div:eq(-1)")
$("div").eq(-1)

(3) 选中第n+1个div元素(n从零开始)
$("div:eq(n)")
$("div").eq(n)
```

综合案例
--------

### 创建表格元素

**练习1：创建单行单列的表格**

```javascript
function createTable1(){
	//1.创建一个table元素
	var $tab = $("<table></table>");
	//2.创建一个tr元素
	var $tr = $("<tr></tr>");
	//3.创建一个td元素, 并为td添加内容
	var $td = $("<td></td>");
	$td.html("Hello TD~~");
	//4.将td添加到tr元素内部
	$tr.append( $td );
	//5.将tr添加到table元素内部
	$tab.append( $tr );
	//6.将table添加到body元素内部
	$("body").append( $tab ); 
	
	//$("body").append( "<table><tr><td>Hello~~TD...</td></tr></table>" );
}
```

**练习2.1：创建单行6列的表格**

```javascript
function createTable2(){
	//1.创建一个table元素
	var $tab = $("<table></table>");
	//2.创建一个tr元素
	var $tr = $("<tr></tr>");
	for(var i=0;i<6;i++){ 
		//3.创建一个td元素, 并为td添加内容
		var $td = $("<td></td>");
		$td.html("Hello TD~~");
		//4.将td添加到tr元素内部
		$tr.append( $td );
	}
	//5.将tr添加到table元素内部
	$tab.append( $tr );
	//6.将table添加到body元素内部
	$("body").append( $tab ); 
}
```

**练习2.2：创建5行6列的表格**

```javascript
function createTable2(){
	//1.创建一个table元素
	var $tab = $("<table></table>");
	for(var j=0;j<5;j++){ //外层循环:控制行数
		//2.创建一个tr元素
		var $tr = $("<tr></tr>");
		for(var i=0;i<6;i++){ //内层循环:控制列数
			//3.创建一个td元素, 并为td添加内容
			var $td = $("<td></td>");
			$td.html("Hello TD~~");
			//4.将td添加到tr元素内部
			$tr.append( $td );
		}
		//5.将tr添加到table元素内部
		$tab.append( $tr );
	}
	//6.将table添加到body元素内部
	$("body").append( $tab ); 
}
```

**练习3：创建指定行和列的表格**

```javascript
function createTable3(){
	//获取用户输入的行数和列数(js方式)
	//var rows = document.getElementById("rows").value;
	//var cols = document.getElementById("cols").value;
	var rows = $("#rows").val();
	var cols = $("#cols").val();
	console.log(rows+" : "+cols);
	//1.创建一个table元素
	var $tab = $("<table></table>");
	for(var j=0;j<rows;j++){ //外层循环:控制行数
		//2.创建一个tr元素
		var $tr = $("<tr></tr>");
		for(var i=0;i<cols;i++){ //内层循环:控制列数
			//3.创建一个td元素, 并为td添加内容
			var $td = $("<td></td>");
			$td.html("Hello TD~~");
			//4.将td添加到tr元素内部
			$tr.append( $td );
		}
		//5.将tr添加到table元素内部
		$tab.append( $tr );
	}
	//6.将table添加到body元素内部
	$("body").append( $tab ); 
}
```

### 仿QQ好友列表

```javascript
/** 通过jQuery实现仿QQ列表好友列表 */
function openDiv(thisobj){ //thisobj是一个js对象 --转成--> jQuery对象
	//先将其他三个分组关闭( 将其他三个分组内的div设置为隐藏 )
	$("table span").not(thisobj).next("div").hide(); //css("display", "none")
	//根据被点击的分组找到分组内的好友列表, 切换好友列表的展示状态
	$(thisobj).next("div").toggle(); //如果元素显示则切换为隐藏, 如果隐藏则切换为显示
}
```

### 模拟员工信息管理系统

练习1：添加员工信息

```javascript
function addEmp(){
	//1.获取要添加的员工信息(id, name, email, salary)
	var id = $("#box1 input[name='id']").val().trim();
	var name = $("#box1 input[name='name']").val().trim();
	var email = $("#box1 input[name='email']").val().trim();
	var salary = $("#box1 input[name='salary']").val().trim();
	console.log(id+" : "+name+" : "+email+" : "+salary);
	
	//2.校验员工信息
	//2.1.添加的员工信息不能为空!
	if( id == "" || name == "" || email == "" || salary == "" ){
		alert( "添加的员工信息不能为空!" );
		return;
	}
	
	//2.2.添加的员工id不能重复! (id=3)
	//获取所有的tr元素, 并遍历所有的tr元素
	var flag = false; //false表示id是不存在的!!!
	$("table tr").each(function(){ //this(JS对象)表示当前被遍历的元素 
		// this --转换为jQuery对象--> $( this ) 
		var _id = $(this).find("td:eq(1)").text();
		//拿着用户输入的id和当前员工的id进行比较
		if( id == _id ){ //只要有一个相等,就说明id已存在,则停止添加
			alert("您输入的员工ID已存在, 请重新添加!");
			flag = true; //true表示id已存在!!
			//return; 放在这里的return不能终止程序的执行
		}
	});
	if( flag ){ //true表示id已存在!!
		return;
	}
	//3.将员工信息添加到页面上(添加到table中)
	//>>创建一个tr元素
	var $tr = $("<tr></tr>");
	//>>创建5个td元素,并将员工信息添加到td中
	var $td1 = $("<td><input type='checkbox'/></td>"); //复选框
	var $td2 = $("<td>"+id+"</td>"); //ID
	var $td3 = $("<td>"+name+"</td>"); //name
	var $td4 = $("<td>"+email+"</td>"); //email
	var $td5 = $("<td>"+salary+"</td>"); //email
	//>>将td元素添加到tr中
	$tr.append( $td1 ).append( $td2 ).append( $td3 ).append( $td4 ).append( $td5 );
			
	//>>将tr元素添加到table中
	$("table").append( $tr );
}
```

练习2：删除员工信息

```javascript
function delEmp(){
	//1.获取所选中员工所在的tr行 (获取所有被选中的复选框)
	//$("input:checked").parents("tr").remove(); //会连接表头一起删除
	$("input:checked").parent("td").parent("tr").remove();
}
```

练习3：修改员工信息（自己完成）

练习4：实现全选或全不选

```javascript
function checkAll(){
	//1.获取全选复选框的选中状态( 选中(true)?  没选中(false)? )
	var isCheck = $("#all").prop("checked"); //true|false
	//2.获取所有普通复选框, 将全选框的选中状态设置给所有普通复选框
	$("input[type='checkbox'][id!='all']").prop("checked",isCheck);
}
```

jQuery总结
----

### html元素操作

**1、创建元素**

```javascript
$("<div></div>") -- 创建一个div元素，返回的是一个表示div元素的jQuery对象
$("<div>xxxx</div>") -- 创建一个包含内容的div元素，返回的是一个表示div元素的jQuery对象
```

**2、添加子元素**

```javascript
$parent.append( $child ) -- 父元素调用方法添加子元素
$("body").append( "<div>我是新来的...</div>" ); -- 往body元素内部追加一个div子元素
```

**3、删除元素**

```javascript
$("div").remove() -- 删除所有的div元素

JS删除所有div元素：
//获取所有的div元素(返回的是所有div组成的数组)
var divArr = document.getElementsByTagName("div"); //div数组
//遍历div数组,依次删除每一个div元素
var len = divArr.length;
for(var i=0;i<len;i++){
    //通过当前元素的父元素删除当前元素(始终删除第一个)
    divArr[0].parentNode.removeChild( divArr[0] );
}
```

**4、替换元素**

```javascript
$("div").replaceWith("<p>我是来替换的…</p>")
```



### html元素内容和值的操作

```html
<div>
  	这是一个div11元素
    <span>这是一个span元素</span>
    这是一个div1111元素
</div>
```

**1、html()函数 (类似于js中的innerHTML属性)** 

-- 用于获取或设置元素的内容，比如为div、span、p、h1、table、tr、td等元素设置内容

```javascript
$("div").html() -- 获取所有div中的第一个div的内容
$("div").html("xxxx") -- 为所有div设置内容
```

**2、text()函数 (类似于js中的innerText属性，innerText在部分浏览器中不兼容)**

\-- 用于获取或设置元素的文本内容

```
$("div").text() -- 获取所有div中的所有文本内容
$("div").text("xxxx") -- 为所有div设置文本内容
```

**3、val()函数** (类似于js中的value属性)

\-- 获取或设置表单项元素的value值(input/select/option/textarea)

```javascript
$("input").val() -- 获取所有input元素中的第一个input元素的value值
$("input").val(值) -- 为所有的input元素设置value值
```



### 元素属性和css属性操作

```html
<input type="text" name="username" id="inp"/>
```

**1、prop()函数** -- 用于获取或设置元素的属性值

在jQuery1.6版本之后才有这个函数，1.6之前版本的jQuery可以使用attr()函数

```javascript
$("input[type='checkbox']").prop("checked")
-- 获取input复选框的选中状态, 返回true表示复选框为选中状态,返回false表示复选框为取消选中状态
$("input[type='checkbox']").prop("checked", true)
-- 设置所匹配的复选框元素为选中状态

$("#inp").prop("name"); //获取id为inp元素的name属性值, 返回useranme
$("#inp").prop("name","user"); //为id为inp的元素设置name属性值, name属性值就会变成user
```

**2、css()函数** -- 用于获取或设置元素的css属性值

```javascript
$("#div1").css("width") -- 获取id为div1元素的宽度
$("#div1").css("width","200px") -- 设置id为div1元素的宽度为200px
$("#div1").css({
	"width" : "200px",
	"height" : "150px",
	"border" : "5px solid red",
	"background" : "pink"
}); // 设置id为div1元素的宽度为200px、高度为150px、边框以及背景颜色等样式
```

### 其他函数

**1、each() 函数**

```
$(selector).each(function( index,element ){})
-- each()函数可以遍历$(selector)选择器选中的所有元素(即每次都选择器选中的元素中获取一个元素,并执行function 函数)
-- function中的index -- 表示遍历的元素的下标
-- function中的element -- 表示当前正在遍历的元素(也可以通过this获取)
```

**2、show()/hide() 函数**

show() -- 设置元素由隐藏变为显示

hide() -- 设置元素由显示变为隐藏

```javascript
$("div").show() -- 设置所有的div元素为显示
```

等价于:

```javascript
$("div").css("display", "block");

$("div").hide() -- 设置所有的div元素为隐藏
```

等价于:

```javascript
$("div").css("display", "none")
```

**2、toggle()/slideToggle()**

toggle() -- 切换元素的显示状态, 如果元素是显示的, 则切换为隐藏, 否则切换为显示

slidToggle() --切换元素的显示状态, 如果元素是显示的, 则切换为隐藏，否则切换为显示，切换为显示为下拉状态，隐藏为收缩状态。

扩展:为元素绑定点击事件
--------------

以点击事件为例，为元素绑定点击事件的方式为:

**方式1(js版)：**

```javascript
<script>
  function fn(){
    alert("input按钮被点击了...");
  }
</script>
<body>
	<input onclick="fn()" type="button" value="点我~!" />
</body>
```

**方式2(js版)：**

```javascript
<script>
	window.onload = function(){
		//获取id为btn的元素
		var btn = document.getElementById("btn");
		btn.onclick = function(){
			alert("input按钮被点击了...");
		}
	}
</script>
<body>
	<input id="btn" type="button" value="点我~!" />
</body>
```

**方式3(jQuery版)：**

```javascript
<script>
$(function(){
    //当点击btn按钮时,触发点击事件执行其中的函数
    $("#btn").click( function(){
        alert("input按钮被点击了...");
    });
});
</script>
<body>
	<input id="btn" type="button" value="点我~!" />
</body>
```

## jQuery作业

`03-25作业：`

1、复习文档就绪事件函数（掌握什么时候该使用文档就绪事件函数）

2、将课上讲过的选择器练习自己再做一遍！

`03-27作业：`

1、完成jQuery综合案例：

```
(1)创建表格
(2)仿QQ好友分组
(3)模拟员工信息管理系统
```

unit06-tomcat、HTTP
==================

服务器概述
----------

### 什么是服务器?

服务器：分为服务器硬件 和 服务器软件。在硬件服务器（计算机）上安装了服务器软件，才可以对外提供服务。

比如：让其他的计算机来访问当前服务器，为其他的计算机提供服务。

(1) 服务器硬件：是指在互联网上具有独立IP地址的计算机，比如我们自己用的计算机也可以作为服务器使用。

(2) 服务器软件：就是一个计算机程序，比如MySQL服务器软件，tomcat服务器软件。服务器软件分为很多类型，比如：ftp服务器，数据库服务器，web服务器软件，邮件服务器等。



### 什么是Web服务器?

(1) web服务器是指驻留在互联网上的某种类型的计算机程序。当浏览器访问服务器，请求服务器上的文件时，服务器将会处理该请求，并将请求的文件响应给浏览器，并会附带一些信息告诉浏览器如何查看该文件（即文件的类型）

(2) web服务器是可以向 "发出请求的浏览器提供文档" 的程序，比如在访问百度时，其实就是在访问百度的服务器。

![](JAVAWEB-NOTE02.assets/5c04c68bde21aeb7db923c319ba4ae70.png)

tomcat就是一个web服务器软件，是由apache组织提供的一款服务器软件，特点：小巧灵活，免费开源，简单易用。

## tomcat下载、安装、启动、配置

### 下载tomcat服务器

下载地址：http://tomcat.apache.org/

tomcat有很多版本，有解压版 和 安装版，还分windows （还分为32位和64位版）和
linux版，根据自己的需求，选择对应的版本下载。

tomcat服务器运行需要jdk的支持，版本对应为：

```
tomcat5 需要jdk4以上支持
tomcat6 需要jdk5以上支持
tomcat7 需要jdk6以上支持
tomcat8 需要jdk7以上支持
```

### 安装、启动tomcat服务器

**1、安装tomcat服务器**

绿色版解压之后就可以使用(原则：安装的路径中不要包含中文和空格)

![](JAVAWEB-NOTE02.assets/609168f9983f96449b7c33f3ebe1890a.png)

解压后还需要配置JAVA_HOME环境变量，该变量指向jdk的根目录，指定tomcat启动时使用哪一个位置的jdk。

**2、启动tomcat服务器**

-----------------------------------------------------

**如何配置JAVA_HOME环境变量：**

变量名: JAVA_HOME

变量值: C:\Program Files\\Java\\jdk1.8.0_45

\--------------------------------------------------------------------------------

（扩展内容）配置Path变量的两种方式：

方式一：

Path=**C:\\Program Files\\Java\\jdk1.8.0_45\\bin;**xxx;xxx;xxx;

方式二：

JAVA_HOME=C:\\Program Files\\Java\\jdk1.8.0_45

Path=%JAVA_HOME%\\bin;xxx;xxx;xxx;

\--------------------------------------------------------------------------------

**启动、关闭tomcat服务器：**

通过 [tomcat根目录]\bin\startup.bat 可以启动tomcat服务器；

通过 [tomcat根目录]\bin\shutdown.bat 可以关闭tomcat服务器；

**访问测试服务器：**

在tomcat服务器启动后，服务器会默认监听8080端口，可以通过如下地址访问tomcat服务器的主页：

```
http://localhost:8080
```

### 修改tomcat默认端口

![image-20200218164109285](JAVAWEB-NOTE02.assets/image-20200218164109285.png)

tomcat服务器在启动时，默认监听的端口是8080，这意味着，我们在访问tomcat服务器时，就需要在主机名（localhost）或者IP地址（127.0.0.1）等后面加上端口。这样非常不方便。

可以将`8080`端口改为`80`端口，因为80端口非常特殊，可以省略不写（只有80端口可以省略，其他端口可在访问时必须得加上）

修改方法：找到 [tomcat安装目录]\conf\server.xml 文件并打开该文件，将文件中的 69 行的 <Connector> 标签上的 port 属性的值改为 80即可。

```xml
<Connector port="80" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
```

改完后，保存文件，重新启动服务器（只有在服务器启动时，才会重新加载server.xml文件）再次启动的服务器就会监听新的端口。

<img src="JAVAWEB-NOTE02.assets/image-20200218164951343.png" alt="image-20200218164951343" style="zoom:80%;" />



**\*\* 扩展问题：FAQ端口占用问题 \*\*：**

在启动tomcat服务器时，可能会遇到端口占用问题，如下图：

![](JAVAWEB-NOTE02.assets/c6008ed65c694512f4b81a2d9fe1877f.png)

![image-20200218165319049](JAVAWEB-NOTE02.assets/image-20200218165319049.png)

原因分析:

**情况一：**可能是之前的tomcat服务器没有完全关闭，仍然在占用80端口，导致服务器再次启动时，启动失败。

> 解决方式：运行shutdown.bat文件，将tomcat按照正常流程再关闭一次即可。如果再次启动服务器成功，说明问题已解决，否则看情况二。
>

**情况二：**可能是其他程序占用了80端口，导致服务器启动失败。

> 解决方式：打开一个cmd窗口，通过 netstat -ano 命令查看当前系统中活动的进程，找到80端口对应的进程编号（PID），根据进程编号将进程结束即可！
>

```
netstat -ano
```

```
协议  本地地址         外部地址        状态           PID
TCP  0.0.0.0:80      0.0.0.0:0      LISTENING     6520
TCP  0.0.0.0:135     0.0.0.0:0      LISTENING     448
...
```

```
taskkill /f /pid 进程编号
```

## tomcat目录结构

tomcat目录结构介绍

![](JAVAWEB-NOTE02.assets/af86c51c1b50075b001b791487750003.png)

tomcat服务器安装根目录下有很多子目录，这些目录的作用是：

```
bin：用于存放tomcat服务器中批处理文件的目录(xx.bat/xx.sh)
conf：用于存放tomcat服务器中的配置文件的目录(其中server.xml文件是tomcat服务器中非常重要的一个文件。)
lib：用于存放tomcat服务器运行时所依赖的jar包。
logs：用于存放tomcat服务器运行时产生的日志文件(启动tomcat服务器时会打印很多日志信息,这些日志信息还会以文件形式保存到logs目录下)
temp：用于存放tomcat服务器产生的临时文件，tomcat会自己清理，可以忽略该目录
webapps：是localhost【虚拟主机】默认管理的目录，将开发好的【web应用】程序放在webapps目录下，就可以通过浏览器访问localhost主机中的Web资源文件了。
可以简单的理解为：webapps目录就是web资源（html、css、js、图片、jsp等）的存放目录，将web资源文件放在该目录下，就可以通过浏览器来访问。

work：用于存放tomcat服务器产生的工作文件（JSP翻译后的Servlet文件会放在work目录下；session对象序列化后产生的文件也会放在work目录下；）
```

## 虚拟主机和Web应用

![image-20200328095145558](JAVAWEB-NOTE02.assets/image-20200328095145558.png)

总结：

（1）虚拟主机就是tomcat服务器中配置的一个站点，在tomcat服务器中默认提供了一个localhost虚拟主机，这个主机的发布目录是webapps目录，这样意味着，将Web应用放在webapps目录下，就表示发不到了localhost虚拟主机中。

（2）Web应用就是一个存放了很多Web资源（html、css、js、jsp、servlet、图片等）的目录，将Web应用发布到虚拟主机中，就可以通过浏览器来访问Web资源中的资源文件了。

## web应用

### web应用的目录结构

```
news(目录,web应用)
  |-- 其他目录, 放在news根目录或者其他目录中的资源文件,浏览器可以直接访问
  |-- WEB-INF目录, 放在这个目录下的资源文件是受保护的,浏览器不能直接访问(不是不能访问,是不能直接访问) 
  		 |-- classes目录, 用于存放编译后的class文件
  		 |-- lib目录, 用于存放web应用所依赖的jar包
  		 |-- web.xml文件, 用于存放和web应用相关的一些配置（配置Servlet、配置主页、配置session的超时时间等）
```

其中news就是一个目录, 同时也是一个web应用程序, 其中可以包含很多的资源文件。

### 部署web应用到虚拟主机中

直接将Web应用的目录拷贝到虚拟主机所管理的目录下，就发布到了虚拟主机中

例如：将news目录拷贝webapps目录下，由于webapps目录是localhost主机默认管理的目录，所以就相当于将news应用发布到 了localhost主机中。

通过如下路径规则就可以访问localhost主机下的news应用下的资源文件：

```
http://localhost:端口/news/xxx
```

## 扩展内容（了解）

访问tomcat服务器主页：http://localhost

访问news/hello.html：http://localhost/news/hello.html

能否将访问 news/hello.html 的路径缩短一些（比如只通过主机名就可以访问news/hello.html这个网页）

### 配置WEB应用的主页

如果没有将 hello.html 配置为当前Web应用的主页，在访问 hello.html 时的路径为：

```
http://localhost/news/hello.html
```

如果将 hello.html 配置为当前Web应用的主页，再次访问 hello.html 时的路径为：

```
http://localhost/news
```

在上的路径中，/hello.html 这个路径可以加，也可以省略。

将 hello.html 配置为当前应用的主页，方式为：找到 [当前Web应用]/WEB-INF/web.xml文件并打开，在web.xml文件的根标签内部添加如下配置：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
  version="3.1">
  	<welcome-file-list>
			<welcome-file>/hello.html</welcome-file>
			<welcome-file>/hello1.html</welcome-file>
			<welcome-file>/hello2.html</welcome-file>
  	</welcome-file-list>

</web-app>
```

配置完后，需要重启服务器，配置才会生效。



### 配置缺省的(默认的)WEB应用

上面已经将news/hello.html配置为news应用的主页，访问hello.html时路径为：http://localhost/news/

如果不将 news 应用配置为默认的Web应用，在访问 news 下的 hello.html(主页)时的访问路径为:

```
http://localhost/news/
```

如果将 news 应用配置为缺省的（默认的）Web应用，在访问 hello.html(主页)时的路径就变成了：

```
http://localhost/
```

如何将 news 配置为缺省的（默认的）Web应用（缺省Web应用只能有一个）？：

**将Web应用的名字改为一个大写的ROOT**，当前Web应用就是一个默认的Web应用，再访问这个Web应用下的资源文件时，访问的路径中就可以不用写Web应用的名称了。

### 打war包

war包和jar包都是java程序中的一种压缩包格式，如果开发一个Java基础工程，可以将其中编译后的class文件和相关的配置文件打成一个jar包。

可以将一个Web应用打成一个war包，这样做的好处有：

```
(1) 将web应用打成一个war包，传输起来更加方便，而且文件体积会变小。
(2) 将war包发布到服务器中，服务器能识别war包格式，会自动将war包解压发布！
```

**打war包的方法是：**

进入到web应用的目录下，将Web应用目录下的所有子目录和文件全部选中，右键压缩成一个 xxx.zip 包，再把 xxx.zip 改为 xxx.war即可!!

需要注意的是，如果有以下问题，可能会导致war不会自动解压：

```
(1) 在将Web应用打成一个压缩包时，没有打成一个 xxx.zip，而是使用 rar格式或者其他格式,会导致自动解压失败!
(2) 打成的war包的名字 和 已发布的web应用的名字不能冲突,会导致自动解压失败!
(3) war包中包含的目录名和文件名是中文的,也会导致自动解压失败!
```

## HTTP协议概述

### 什么是HTTP协议?

![](JAVAWEB-NOTE02.assets/14bcab6ec3d58f3fea59d35a1c618a16.png)

HTTP协议是用于规定浏览器和服务器之间的通信方式/规则

主要规定了浏览器给服务器发送的请求信息的格式

以及规定了服务器给浏览器发送响应信息的格式



HTTP协议在工作时所遵循的基本原则：

```
（1）一次请求，只对应一次响应
（2）请求只能由浏览器发起，服务器只能被动的等待请求，根据请求作出回应。
```

## HTTP协议详解

IE浏览器的插件：HttpWatch，可以监听浏览器和服务器通信的内容。

### HTTP请求

<img src="JAVAWEB-NOTE02.assets/169364c50b950ea4df4647e274a7298d.png" style="zoom: 80%;" />

**1、请求行**

```
GET  /news/hello.html  HTTP/1.1
```

（1）GET：表示请求方式，在HTTP协议中一共定义了7种提交方式，但是我们只用GET和POST。

（2）/news/hello.html：请求资源路径，表示浏览器请求的是哪一个Web应用以及哪一个web资源文件。

（3）HTTP/1.1：请求所遵循的协议和版本。

**2、若干请求头**

请求头都是Key-Value结构,例如：

![image-20200219143453111](JAVAWEB-NOTE02.assets/image-20200219143453111.png)

```
Host：localhost -- 通知服务器，浏览器要请求的是哪一台虚拟主机。
Accept：text/html, appliaction/xhtml+xml,...  -- 通知服务器，浏览器能接收的响应数据类型。
...
```

（空白行，用于分隔请求头和请求实体）

**3、请求实体内容**

如果请求方式为 GET 提交，请求实体是没有内容的！

如果请求方式为 POST 提交，并且请求中携带了数据，请求实体中才会有内容！



### HTTP响应

![](JAVAWEB-NOTE02.assets/08e49b1b985988b040fe437d4aab7e62.png)

**1、状态行**

```
HTTP/1.1 200 OK
```

（1）HTTP/1.1：表示响应所遵循的协议和版本

（2）200：状态码，三位的数字，表示服务器对请求处理的结果。

```
	200: 表示请求处理成功
	302: 表示请求重定向(即需要再进一步请求才可以获取到相应的资源)
	304/307: 表示通知浏览器使用缓存
	404: 表示浏览器请求的资源不存在(浏览器的问题, 请求路径错误)
	500: 表示服务器在处理请求的过程中抛出了异常。
```

（3）OK：描述短语（可以忽略），也表示服务器对请求处理的结果，和状态码表示的结果一致。

```
	200：OK
	404：Not Found
	500: Internal Server Error
	...
```

**2、若干响应头**：也是key-value格式

```
Content-Type: 表示服务器响应的数据类型，text/html,  image/*...
Content-Length: 表示服务器响应数据的长度, 例如: 384 /字节
Set-Cookie: 和cookie技术相关的一个头, 后面会提到。
...
```

**3、响应实体内容**

响应实体就是浏览器所请求文件的内容。例如：浏览器向服务器请求一个hello.html文件，服务器会找到hello.html文件，将文件的内容作为响应实体发送给浏览器。



### 内容补充

**1、问题1：请求方式什么时候是GET提交？什么时候是POST提交？**

只有当使用表单（form），并且在表单上明确的通过method指定提交方式为POST时，请求方式才是POST提交，其他方式都是GET提交（AJAX除外）

**思考：判断以下请求方式是GET还是POST?**

```
(1)<form action="#"></form>											--- GET提交
(2)<form action="#" method="GET"></form>				--- GET提交
(3)<form action="#" method="POST"></form>				--- POST提交
(4)点击超链接访问服务器，例如：
	<a href="http://www.baidu.com">百度一下</a>		--- GET提交
(5)直接在浏览器的地址栏中书写URL地址访问服务器				--- GET提交
```

**2、问题2：GET提交和POST提交有什么区别？**

主要体现在请求参数传输过程的不相同

GET提交：

- 将数据通过问号拼接在地址栏URL地址的后面，相对非常不安全。
- 将数据拼接在地址栏URL地址的后面，数据量是有限制的，通常不能超过1KB或者4KB。

POST提交：（form）

- POST提交是通过请求实体将数据提交给服务器，不会显示在地址栏上，因此相对更加安全。
- POST提交通过请求实体提交数据，数据量理论上是没有限制的。

**3、总结：**

- 如果只是单纯做一个跳转，请求中没有数据，尽量使用GET提交。
- 如果在请求中有数据，但数据量不大，并且数据没有隐私性，也尽量使用GET提交。
- 如果在请求中有数据，数据量比较大或者数据较为隐私，此时推荐使用POST提交。

## 将Tomcat整合到Eclipse中

将Tomcat服务器整合到Eclipse工具中，可以通过Eclipse启动、关闭tomcat服务器，更重要的是，可以非常方便的将在Eclipse中创建的Web项目发布到Tomcat服务器中运行。

### 方式一：在window偏好设置中配置Tomcat

1、点击Window --> Preferences(偏好设置):

![image-20200311184907773](JAVAWEB-NOTE02.assets/image-20200311184907773.png)

2、在偏好设置窗口中点击 Server --> Runtime Environments --> add:

![image-20200311184913436](JAVAWEB-NOTE02.assets/image-20200311184913436.png)

3、在弹出的窗口中选择 --> Apache --> Apache Tomcat v8.5，需要注意的是，这里得根据自己安装的tomcat版本进行选择，比如我安装是8.5版本的tomcat，所以这里选择Apache Tomcat v8.5。

![image-20200311184921087](JAVAWEB-NOTE02.assets/image-20200311184921087.png)

4、在下面的窗口中配置tomcat服务器的安装根目录，可以直接把路径复制到第二个输入框中；也可以点击后面的 Browse按钮在文件管理器中选择tomcat服务器安装根目录。

![image-20200311184932405](JAVAWEB-NOTE02.assets/image-20200311184932405.png)

最后点击finish即可完成将Tomcat整合到Eclipse中的配置。

### 方式二：在创建Web项目时配置Tomcat

1、如果在创建Web项目时，Target runtime选项中没有配置可选的服务器，可以点击右面的选项进行配置

点击后进入下一步操作。

![image-20200311184950046](JAVAWEB-NOTE02.assets/image-20200311184950046.png)

2、在弹出的窗口中选择 --> Apache --> Apache Tomcat v8.5，需要注意的是，这里得根据自己安装的tomcat版本进行选择，比如我安装是8.5版本的tomcat，所以这里选择Apache Tomcat v8.5。

![image-20200311185003036](JAVAWEB-NOTE02.assets/image-20200311185003036.png)

3、在下面的窗口中配置tomcat服务器的安装根目录，可以直接把路径复制到第二个输入框中；也可以点击后面的 Browse按钮在文件管理器中选择tomcat服务器安装根目录。

![image-20200311185013454](JAVAWEB-NOTE02.assets/image-20200311185013454.png)

最后点击finish即可完成将Tomcat整合到Eclipse中的配置。

4、上一步完成后，回到Web项目创建的视图窗口，再查看"Target runtime"选项，如下：

![image-20200311185028965](JAVAWEB-NOTE02.assets/image-20200311185028965.png)

### 将整合到Eclipse中的tomcat从Eclipse中删除

如果要将整合到Eclipse中的tomcat从Eclipse删除：点击Windows --> Preferences --> Server --> Runtime Environments，选中要删除的服务器，点击右侧的删除按钮即可删除，最后点击Apply and Close保存设置即可！

![image-20200311185037713](JAVAWEB-NOTE02.assets/image-20200311185037713.png)

### 在Eclipse中创建Server及移除Server

上面讲解了如何将Tomcat整合到Eclipse中，整合之后，需要在Eclipse中创建一个Server才可以进行启动tomcat、关闭tomcat等操作。

1、Eclipse中找到Servers窗口：

![](JAVAWEB-NOTE02.assets/53ee068642a0174e038b8d61fe0791e8.png)

2、如果没有可以到Window --\> Show View --\> Other中搜索"servers"，如下图:

![](JAVAWEB-NOTE02.assets/4c3f46765ddae7d3cac4287efe14fa6e.png)

![](JAVAWEB-NOTE02.assets/cf2948fcf3af5900fc2b70f8769e9b05.png)

3、在Server窗口中点击“No servers are available…”链接：

![](JAVAWEB-NOTE02.assets/ba09d4090bccbc59c3d1057bcab8d07d.png)

4、在弹出的窗口中，保持默认配置，直接点击完成

如果弹出的窗口中默认的服务器不是tomcat，则说明在此之前没有将Tomcat整合到Eclipse中。

![](JAVAWEB-NOTE02.assets/08e1747f402c1be68ae9cf62ee7719e0.png)

5、在上一步点完成后，Eclipses左侧会多出一个Servers项目，Servers窗口中会出现创建的Server，也就是tomcat服务器。

注意：①处的Servers项目不能关闭（close），更不能删除（delete）

![](JAVAWEB-NOTE02.assets/dfd52724dc14ed43f7c48ca16ac85da4.png)

6、在创建完Server后，双击tomcat，可以修改Tomcat服务器配置

(1)将Server Locations中的选项切换为第二个选项

(2)将Deploy Path右侧的输入框中的内容改为webapps。ctrl+s保存配置即可

![image-20200328164951699](JAVAWEB-NOTE02.assets/image-20200328164951699.png)

以上配置是为了保证在Eclipse中发布Web应用到tomcat服务器中时，可以将项目发布到tomcat服务器的webapps目录下。

如果不配置，会导致tomcat服务器中webapps下的Web应用无法访问。

![](JAVAWEB-NOTE02.assets/28b8712f4f5114a24acde35017275a93.png)

7、如果要移除添加的Server，需要同时删除①处的Servers项目（右键delete，要彻底从硬盘上删除），以及删除②处的tomcat服务器（右键delete）

![](C:/Users/zhangsz/Desktop/media/dfd52724dc14ed43f7c48ca16ac85da4.png)

### tomcat右键选项介绍

![](JAVAWEB-NOTE02.assets/1eec7770246693752b0eaa984ca7e92c-1584273824888.png)

a) Start：用于启动tomcat服务器，如果已启动，则显示 ReStart，作用是重启服务器

b) Stop：用于停止服务器

c) Add and Remove：将Web应用部署到tomcat服务器中，或者移除服务器中部署的Web应用

d) Clean：作用是将发布到Eclipse自己的webapps目录中的项目删除再重新部署

e) Clean Tomcat Work Directory：作用是将在tomcat运行过程中存入work目录的文件删除

### tomcat启动失败常见原因

**问题1：tomcat服务器启动失败-1**

如果在启动服务器时，服务器启动失败，并弹出窗口显示如下异常信息：

![](JAVAWEB-NOTE02.assets/25c037cb7399daf7127195a451115c07-1584273824889.png)

根据上面的描述信息，可以看出是8005、8080、8009端口被同时占用了，此时只有一种可能，就是之前已经启动了tomcat或者之前开启的tomcat没有完全关闭导致的。

解决方式：到tomcat安装目录找到bin目录中的shutdown.bat文件，双击运行将服务器关闭，再到Eclipse中启动服务器即可！

**问题2：tomcat服务器启动失败-2**

如果在启动服务器时，服务器启动失败，并弹出窗口显示如下异常信息：

![](JAVAWEB-NOTE02.assets/d4e3c02075eb7f39ac1ea72e31aab137-1584273824889.png)

**解决方法：**

(1) 可以先将服务器中所有的Web应用移除（在服务器上右键，**Add and Remove**--\>**Remove All**--\>**Finish**）

(2) 再分别执行服务器右键选项中的**clean**和**Clean Tomcat Work Directory**

(3)再次启动服务器，如果启动没有报错，则说明tomcat服务器本身没有问题，再将要运行的项目发布到tomcat中，再次启动服务器，观察是否有错误。如果有则说明是项目本身的问题。

(4)如果移除了所有的Web应用，启动tomcat服务器报错，则说明tomcat本身就有问题，可以将tomcat服务器重新配置一次到Eclipse中(将tomcat和Server项目删除，再点击链接重新创建Server)

unit07-Servlet
================

Servlet概述
-----------

### 什么是Servlet?

Servlet是由SUN公司提供的一门动态Web资源开发技术

Servlet本质上是一段Java程序，和之前的Java程序不同的是，Servlet程序无法独立运行，需要将Servlet程序放在服务器中（比如tomcat服务器），由服务器调用才可以执行。

Servlet: 服务器端的Java程序.

Servlet是运行在服务器端的Java程序，其作用是什么？

其作用是对服务器接收过来的请求进行处理（作用为处理请求）

![](JAVAWEB-NOTE02.assets/329ebdac1b25e0943488cf41428e6552.png)

开发Servlet程序
---------------

### 开发Servlet程序的步骤

第一步: 写一个类，实现一个Servlet接口或者继承Servlet接口的子类（GenericServlet/HttpServlet），并实现其中的方法

```
Servlet接口
	|-- GenericServlet类(抽象类)
				|-- HttpServlet类
```

第二步: 在web应用的web.xml文件中配置Servlet程序对外访问的路径。

Eclipse在创建一个Servlet时，会在web.xml文件中生成Servlet配置，所以不需要我们手动配置。

### 使用Eclipse创建Web项目

![](JAVAWEB-NOTE02.assets/22432d0ee6fe5616365ecb77f5748b37.png)

![](JAVAWEB-NOTE02.assets/46a097af287c3d455ace4644c98ad27b.png)

以上是Web项目在工程视图(Project)和包视图（package）下结构，推荐使用包视图！

**1、创建一个Web工程:** 在左侧窗口中, 点击**鼠标右键** ---\> **New** ---\>
**Dynamic Web Project**。

![](JAVAWEB-NOTE02.assets/22fa5f600a0bdd2206b028c42d7feab3.png)

**2、接着会弹出如下窗口:**

![创建Web项目](JAVAWEB-NOTE02.assets/f534b2420e73dc56b14042eb95c91cc0.png)

**注意：**

(1) 3.0版本不会创建web.xml文件,
并且创建Servlet时也不会在web.xml文件中生成Servlet相关的配置信息, 记得改为2.5。

(2) Target runtime选项中如果没有可选的服务器，可点击右侧的"New
Runtime…"进行配置。

详细操作步骤在《5.2配置Target runtime（Web项目运行环境）》

**3、Eclipse中创建的Web工程的目录结构：**

![image-20200219170618551](JAVAWEB-NOTE02.assets/image-20200219170618551.png)

```
(1) day09: 工程名称/项目名称
(2) src: 源码目录, 创建的java源文件、配置文件（properties、xml文件等）都可以放在src源码目录下
(3) build/classes: 编译文件的输出目录, src源码目录中的文件编译后会输出到classes目录下。
	其中的classes目录在发布时会放在WEB-INF目录下，随着项目一起发布到服务器中
(4) WebContent: 就是Web应用的目录，其中可以存放 html、css、js、jsp、图片以及编译后的class文件、jar包、web.xml文件等. 将来发布项目到服务器，其实就是将WebContent中的所有内容一起发布到服务器中。
(5) WebContent/WEB-INF/lib: 用于存放当前项目所依赖的jar包。比如要访问mysql数据库，需要导入mysql驱动包，直接将jar包拷贝到lib目录下即可！（也不用再去做 build path --> add to build path）
```



### 使用Eclipse创建Servlet

1、选中项目中的src目录，鼠标右键 ---\> New ---\> Servlet

![](JAVAWEB-NOTE02.assets/b363459bbe88da812109f0863d80b552.png)

2、在弹出的窗口中，根据提示填写内容：

![](JAVAWEB-NOTE02.assets/4226a1514a967a42ec6d49e23b725939.png)

3、点击finish即可完成Servlet创建过程, 创建好的Servlet如下:

![](JAVAWEB-NOTE02.assets/3d2214e9146db1b26b6038f61c3a8014.png)

通过Eclipse创建Servlet，默认继承HttpServlet。由于HttpServlet也是Servlet接口的子类，让HelloServlet继承HttpServlet，相当于间接实现了Servlet接口。

继承HttpServlet类，默认会覆盖doGet方法和doPost方法，两个方法的作用为：

**\* doGet方法：**当浏览器发送请求的方式为GET提交时, 将会调用doGet方法来处理请求

**\* doPost方法：**当浏览器发送请求的方式为POST提交时,
将会调用doPost方法来处理请求

提示：如果当GET提交和POST提交处理代码相同时，可以将代码写在其中一个方法里（例如写在doGet中），并在另外一个方法（例如doPost）中调这个方法。这样一来,不管是GET提交还是POST提交,最终doGet方法都会执行,都会对请求进行处理!!

### Servlet在web.xml中的配置

在通过Eclipse创建Servlet时，会自动在web.xml文件中进行Servlet相关信息的配置

（注意：如果是复制Servlet类文件，但配置信息不会跟着复制，需要自己手动添加配置，否则复制的Servlet将无法访问！）

```xml
<servlet>
    <servlet-name>HelloServlet</servlet-name>
    <servlet-class>com.tedu.HelloServlet</servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>HelloServlet</servlet-name>
    <url-pattern>/HelloServlet</url-pattern>
</servlet-mapping>
```

**关于上面的配置信息：**

**a)** Eclipse每创建一个Servlet,
就会在web.xml文件中添加两个标签：\<servlet\>和\<servlet-mapping\>标签（可以将这两个标签看成一个组的标签）

**b)**
\<servlet\>和\<servlet-mapping\>标签内都会有一个\<servlet-name\>标签，标签的内容可以更改，但要求更改后的这两个\<servlet-name\>标签的内容也必须一致。

**c)** \<servlet-class\>标签用于配置Servlet类的全路径名(即包名+类名)

需要注意：如果在创建Servlet后修改了Servlet类的名称，这个地方也要一起更改，否则将会出现"ClassNotFoundException"
即类找不到异常

**d)**
\<url-pattern\>标签用于配置浏览器以什么路径访问当前Servlet（即Servlet对外访问的路径），默认的路径是：/类名

例如：上面为HelloServlet配置的\<url-pattern\>为
**/HelloServlet**，因此我们在浏览器中的访问路径则为：

[http://主机名/web](http://主机名/web)项目访问路径**/HelloServlet**

### 运行Servlet程序、访问测试

**1、访问Servlet方式一：**

若是第一次运行，需要先创建tomcat服务器，即在Servers窗口中点击链接可创建一个tomcat服务器，且只需创建一次即可！

(1)发布项目到服务器：在服务器上右键 --\> 点击 "**add and remove"** 将当前web项目发布到服务器中，并点击完成。

(2)启动tomcat服务器：在服务器上右键 Start 即可启动服务器

(3)通过浏览器访问Servlet：打开本地浏览器，通过路径访问，即可访问Servlet程序

`http://localhost:8080/项目名称/HelloServlet`

**2、访问Servlet方式二：**

**(1) 在运行的Servlet上点击右键 --**-\> **"Run As"** ---\> **"1 Run on Server"**

![](JAVAWEB-NOTE02.assets/329006b7629a8f0b0c9bddfc90fba675.png)

(2) 在弹出的窗口中，直接点击完成即可！！！

![](JAVAWEB-NOTE02.assets/6340e1bd76974184a91c55595864123b.png)

(3) 运行结果如下：

![](JAVAWEB-NOTE02.assets/f478e638564b90f44fdd1ef210c11f30.png)

或者打开浏览器，复制上图中的路径：

http://localhost:8080/Hello/HelloServlet，粘贴到浏览器的地址栏中，回车访问：

![](JAVAWEB-NOTE02.assets/12910389bb2a950777329cc3568e8ec7.png)

### Eclipse默认发布Web应用的位置

Tomcat服务器中默认只有一台虚拟主机,叫做localhost主机

而localhost主机发布web应用的位置是webapps。

将day09发布到localhost主机中,但为什么day09项目没有在webapps目录下?

\--------------------------------------------------------------------------------------------------------

默认情况下,发布一个Web应用到localhost主机中，只需要将Web应用的目录拷贝到webapps目录下即可完成发布!

而将Eclipse和Tomcat整合之后，通过Eclipse发布一个web应用到tomcat服务器中，发布的路径默认被改成了:

[工作空间]\\.metadata\\.plugins\\org.eclipse.wst.server.core\\tmp0\\wtpwebapps

**如何修改Eclipse默认发布Web应用的目录位置:**

(1)关闭服务器,将服务器中的所有应用移除

(2)在服务器上右键 --\> clean

(3)双击tomcat服务器,在弹出窗口中找到 Server location, 选择第二个选项

并将下方的Deploy Path改为: webapps 改完后，Ctrl+s保存配置即可!!

### Eclipse如何发布一个Web应用

当通过eclipse将day09项目发布到服务器中,是直接将day09拷贝到服务器中对应的目录下吗?

发布的过程如下：

<img src="JAVAWEB-NOTE02.assets/66b1236906843df1bfc1d002a36a0ea7.png" style="zoom: 50%;" />

Servlet调用过程
---------------

通过浏览器访问服务器中的一个Servlet程序，这个Servlet程序是如何执行的？又是如何被调用的？

localhost/Hello/HelloServlet

参考<<Servlet调用过程图>>

扩展:修改Servlet模版
--------

通过Eclipse可以直接创建一个Servlet类，这相比通过记事本等文本编辑工具创建Servlet，可以节省配置Servlet的时间，提高了我们的开发效率。

但是通过Eclipse生成的Servlet类中包含了许多我们不需要的注释和默认实现代码，这些每次都删除也非常占用时间。

接下来可以通过添加模版代码的形式，来生成Servlet的内容，以便于提高我们的开发效率。

**1、先创建一个Servlet，将其中的内容修改为自己期望的模版格式，并复制其中的内容，例如：**

```java
package ${enclosing_package};

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * author: bjzhangsz@tedu.cn
 * datetime: ${date} ${time}
 */
public class ${primary_type_name} extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html;charset=utf-8");
		PrintWriter out = response.getWriter();
	}
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doGet(request, response);
	}
}
```

**2、点击菜单栏中的window --\> Preferences**：

![](JAVAWEB-NOTE02.assets/61ff91aedf878c76b0e51b94ffdca92a.png)

**3、在出现的窗口左侧依次点击：Java --\> Editor --\> templates
--\>(在右边的窗口中) 点击New… ：**

![](JAVAWEB-NOTE02.assets/35b3781ebd2acd7a178db29783dc5a6a.png)

**4、在出现的新窗口中填写如下内容：**

![](JAVAWEB-NOTE02.assets/7dcab79636bff53d51b35d449adffebd.png)

**5、替换包路径和类名（作用是在新建Servlet生成的Servlet模版中使用当前类的包路径和类型）**

![](JAVAWEB-NOTE02.assets/cfc14076c3b3e9187afa6594a5ba08a8.png)

效果如下：

![](JAVAWEB-NOTE02.assets/82d8ec98345ff6e99c7caf7fce40c38f.png)

![](JAVAWEB-NOTE02.assets/3e4ab784b24d0682572a1d92ec58098e.png)

效果如下：

![](JAVAWEB-NOTE02.assets/a7026f1287e078eb5561ff5ff7ff2ebe.png)

**6、点击OK保存，创建新的Servlet文件，测试**：

将Servlet中的所有内容全选删除，并输入"servlet"，接着按 "Alt+ /"
提示即可生成自己想要的Servlet模版内容!

![](JAVAWEB-NOTE02.assets/0f1925b9e96b93a6e13e7aa674ec2e35.png)

效果如下:

![](JAVAWEB-NOTE02.assets/a5ada366c84bcef88e797f7126db4433.png)



request和response介绍
---------------------

request是代表HTTP请求信息的对象，response是代表HTTP响应信息的对象。

当浏览器发请求访问服务器中的某一个Servlet时，服务器将会调用Servlet中的service方法来处理请求。在调用service方法之前会创建出request和response对象。

其中request对象中封装了浏览器发送给服务器的请求信息（请求行、请求头、请求实体等），response对象中将会封装服务器要发送给浏览器的响应信息（状态行、响应头、响应实体），在service方法执行完后，服务器再将response中的数据取出，按照HTTP协议的格式发送给浏览器。

每次浏览器访问服务器，服务器在调用service方法处理请求之前都会创建request和response对象。（即，服务器每次处理请求都会创建request和response对象）

在请求处理完，响应结束时，服务器会销毁request和response对象。

request对象
-----------

### 获取请求参数

**问题1、什么是请求参数？**

所谓的请求参数，就是浏览器发送给服务器的数据（不区分请求方式），例如：通过表单向服务器提交的用户名、密码等，或者在超链接后面通过问号提交的数据，都是请求参数。

```
http://localhost/day10/TestParam?user=zhangsan&pwd=123&like=篮球&like=足球
```

**问题2、如何获取请求参数？**

```
(1)request.getParameter(String paramName)
-- 根据请求参数的名字获取对应的参数值，返回值是一个字符串；
-- 如果一个参数有多个值，该方法只会返回第一个值。
-- 如果获取的是一个不存在的参数，返回值为null
(2)request.getParameterValues(String paramName)
-- 根据请求参数的名字获取该名字对应的所有参数值组成的数组，返回值是一个字符串数组，其中包含了这个参数名对应的所有参数值
-- 如果获取的是一个不存在的参数，返回值为null
```

代码示例：

```java
//1.获取请求参数中的用户名(user)
String user = request.getParameter("user");
System.out.println( "user="+user );

//2.获取请求参数中的爱好(like)
String[] like = request.getParameterValues( "like" );
System.out.println( "like="+Arrays.toString( like ) );
```

**问题3、获取请求参数时的中文乱码问题？**

在获取中文的请求参数时，可能会出现乱码问题（和请求方式、tomcat服务器版本有关），具体可以分为以下三种情况：

（1）如果请求是GET提交，并且tomcat是8.0及以后的版本，GET提交的中文参数，在获取时不会出现乱码问题！（8.0以后的tomcat包括8.0在获取GET提交的中文参数时，已经处理中文乱码问题。）

（2）如果请求是POST提交，不管是哪个版本的tomcat服务器，在获取中文参数时，都会出现乱码问题。因为tomcat底层在接收POST提交的参数时，默认会使用iso8859-1编码接收，而这个编码中没有中文字符，所以在接收中文参数时，一定会出现中文乱码问题！

解决方法是：通知服务器在接收POST提交的参数时，使用utf-8编码来接收!

```java
request.setCharacterEncoding("utf-8");
```

注意：这行代码不会影响GET提交，只对POST提交有效！

这行代码要放在任何获取参数的代码之前执行！

（3）如果请求是GET提交，并且tomcat是7.0及以前的版本，GET提交的中文参数，在获取时会出现乱码问题！

解决方法：在[tomcat安装目录]/ conf/server.xml文件的(修改端口的)Connector标签上，添加一个 URIEncoding="utf-8" 属性，如下：

```xml
<Connector port="80" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443"
           URIEncoding="utf-8" />
```

同时在[Eclipse]/Servers/[当前tomcat服务器对应的配置目录]/server.xml文件中，在Connector标签上，添加一个 URIEncoding="utf-8" 属性，同上！

### 实现请求转发

请求转发是服务器内部资源的一种跳转方式，即当浏览器发送请求访问服务器中的某一个资源（A）时，该资源将请求转交给另外一个资源（B）进行处理并且由资源B做出响应的过程，就叫做请求转发。

请求转发和重定向都是资源的跳转方式，但是跳转的过程有所不同。

![image-20200304232156159](JAVAWEB-NOTE02.assets/image-20200304232156159.png)

**请求转发的特点：**

```
（1）转发是一次请求，一次响应
（2）请求转发前后，浏览器的地址栏地址不会发生变化。（浏览器--访问--> A --转发--> B，地址栏地址始终指向A的地址）
（3）请求转发前后的request对象是同一个（转发前在A中的request和转发到B后，B中的request对象和A中的request对象是同一个。基于这一点，可以通过request从A带数据到B）
（4）请求转发前后的两个资源必须属于同一个Web应用，否则将无法进行转发。（A--转发-->B，A和B必须属于同一个Web应用！）
```

**请求转发实现:**

```java
request.getRequestDispatcher(url地址/转发到资源的地址).forward(req, res);
```

**代码示例：**

```java
//从当前Servlet转发到 index.jsp(http://localhost/day10/index.jsp)
//request.getRequestDispatcher("/index.jsp").forward(request, response);
request.getRequestDispatcher("index.jsp").forward(request, response);
```

<img src="JAVAWEB-NOTE02.assets/image-20200221171059404.png" alt="image-20200221171059404" style="zoom:67%;" />

### 作为域对象使用

request在实现转发时，通过request.setAttribute方法和request.getAttribute方法带数据到目的地时，就是通过request对象中的map集合带数据，这个request对象上的map集合以及request对象所在的范围即称之为是一个域对象。

如果一个对象具备可以被访问的范围，通过这个对象上的map集合可以在整个范围内实现数据的共享。这样的对象就叫做域对象。

在request对象上提供了往域对象(map)中存数据的方法以及取数据的方法：

```java
request.setAttribute(String attrName, Object attrValue);
-- 往request域中存入一个域属性，属性名（key）只能是字符串,属性值(value)可以是任意类型。
request.getAttribute(String attrName);
-- 根据属性名(key)获取对应的属性值(value)。返回的是一个Object类型的对象。
```

**request域对象所具备的三大特征:**

**生命周期：**在服务器调用Servlet程序的service方法之前，会创建代表请求的request对象，在请求处理完，响应结束时，会销毁request对象。

**作用范围：**在一次请求范围内，都可以获取到同一个request对象。

**主要功能：**和请求转发配合使用，从Servlet带数据到JSP（带数据到目的地）



**扩展内容：**request对象的getParameter和getAttribute方法有什么区别?

- getParameter()方法是用于获取(从浏览器发送过来的)请求参数的，请求参数不能设置，只能是浏览器发送给服务器，在服务器端再通过getParameter方法获取请求中的参数
- getAttribute()方法是用于从request域中获取域属性时用的，域属性得先存入到域中（即得先通过setAttribute方法将数据存入request域中），再通过getAttribute()方法从域中获取。



### 案例:模拟查询所有门店功能

**1、创建一个Servlet程序，用于处理查询所有门店信息请求**

```java
public class DoorListServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
	protected void doGet(HttpServletRequest request, HttpServletResponse
response)
throws ServletException, IOException {
        response.setContentType("text/html;charset=utf-8");
        PrintWriter out = response.getWriter();
        //1.模拟查询数据库, 查询所有门店集合
        List<String> doorList = new ArrayList();
        doorList.add("01, 永和北三环西路店, 010-67676767");
        doorList.add("02, 永和西直门店, 010-68976347");
        doorList.add("03, 永和东直门店, 010-78397647");
        doorList.add("04, 永和北京西店, 010-78764397");
        doorList.add("05, 永和天安门店, 010-78769743");
        //2.将数据存入request域中
        request.setAttribute( "list", doorList );
        //3.将请求转发到 door_list.jsp 中, 取出所有门店显示在页面中
        request.getRequestDispatcher("door_list.jsp")
        .forward(request, response);
    }
}
```

**2、创建一个JSP，用于显示所有门店信息**

```jsp
<body>
<h3>显示所有门店信息</h3>
    <%
        //获取request域中的门店信息集合
        List<String> list =(List<String>)request.getAttribute("list");
        //遍历门店集合, 将门店信息输出在网页上
        for( String door : list ){
        	out.write( door +"<br/>");
        }
    %>
</body>
```

response对象
------------

response是代表HTTP响应信息的对象。

### 向客户端发送数据

PrintWriter out = response.getWriter();

由于服务器在通过response获取的流发送数据时，默认使用iso8859-1编码，而这个编码中没有中文字符，所以在通过response获取的流发送中文数据时，会出现乱码问题。

解决方法是：在响应数据之前，通知服务器使用utf-8发送数据。

```java
/*  通知服务器在响应数据时,使用utf-8编码
 * 也能通知浏览器使用utf-8接收服务器发送的数据 */
response.setContentType( "text/html;charset=utf-8" );
PrintWriter out = response.getWriter();
out.write( "你好" );
```

### 实现重定向

当浏览器向服务器发请求访问某一个资源A，资源A在响应时通知浏览器需要再进一步请求才能获取到对应的资源，浏览器再次发请求访问服务器中的资源B，最终由资源B响应浏览器要获取的资源，这个过程叫做重定向。

![image-20200304232136926](JAVAWEB-NOTE02.assets/image-20200304232136926.png)

**重定向的特点：**

```
（1）重定向是两次请求、两次响应
（2）重定向前后，浏览器的地址栏地址会发生变化。（因为两次请求都是通过浏览器发起，浏览器知道这个跳转的过程，因此地址栏地址会变化）
（3）重定向前后的request对象不是同一个（因为重定向是两次请求，服务器会根据两次请求创建两个不同的request对象，request对象不是同一个，也就不能在重定向时通过request带数据到目的地。）
（4）重定向前后的两个资源可以是来自不同的web应用，甚至可以是来自不同的服务器。(进行跳转的两个资源之间没有限制)
```

**实现代码：**

```java
response.sendRedirect(所重定向到资源的URL地址);
```

**代码示例：**

```java
//测试1: 从当前Servlet（day10/TestRedirect）重定向到day10/index.jsp
// http://localhost/day10/TestRedirect
// http://localhost/day10/index.jsp
response.sendRedirect( "http://localhost/day10/index.jsp" );
response.sendRedirect( "/day10/index.jsp" );
response.sendRedirect( "/index.jsp" ); //错误路径
response.sendRedirect( "index.jsp" ); //正确路径

//测试2: 从当前Servlet重定向到day09/index.jsp
response.sendRedirect( "http://localhost/day09/index.jsp" );

//测试3: 从当前Servlet重定向到百度首页
response.sendRedirect( "http://www.baidu.com" );
```

总结：什么时候用转发（forward）？什么时候用重定向（redirect）？

```
(1)如果希望跳转前后地址栏地址不会发生变化, 只能使用转发; 如果希望跳转前后地址栏地址会发生变化, 只能使用重定向
(2)如果希望在跳转前后, 能够通过request对象带数据到目的地, 只能使用转发
(3)如果仅仅是做一个跳转,没有其他要求,此时推荐使用转发(转发是一次请求,一次响应,可以减少访问服务器的次数,降低服务器的压力)
```

## servlet作业

`03-30作业：`

(1) 练习request对象获取请求参数(regist.html、TestParam2)

(2)练习请求转发+域对象

(3)完成《Servlet、request、response练习题》