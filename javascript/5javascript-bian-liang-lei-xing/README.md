# 5、JavaScript变量类型



## JavaScript变量类型 <a id="javascript&#x53D8;&#x91CF;&#x7C7B;&#x578B;"></a>

avaScript 是一种弱类型或者说动态语言。这意味着你不用提前声明变量的类型，在程序运行过程中，类型会被自动确定。这也意味着你可以使用同一个变量保存不同类型的数据.

最新的 ECMAScript 标准定义了 7 种数据类型:Boolean、Null、Undefined、Number、String、Symbol[2](https://yangjh.gitee.io/front-end/js/jstype.html#fn_2) 和Object。

### Boolean布尔型 <a id="boolean&#x5E03;&#x5C14;&#x578B;"></a>

布尔型数据的取值只有两个：true和false。布尔型数据不能用引号括起来，否则就变成字符串了。

```text
var a = false; //boolean类型
var b = 'false'; //字符串类型
```

### Null空类型 <a id="null&#x7A7A;&#x7C7B;&#x578B;"></a>

值 null 是一个 JavaScript 字面量，表示空值（null or an "empty" value），即没有对象被呈现（no object value is present）。

### Undefined未定义类型 <a id="undefined&#x672A;&#x5B9A;&#x4E49;&#x7C7B;&#x578B;"></a>

一个未初始化的变量的值为undefined,使用严格相等运算符\(===\)来判断一个值是否是undefined:

```text
var x;
alert(typeof x);
```

### Number数值型 <a id="number&#x6570;&#x503C;&#x578B;"></a>

在Javascript中，数值型数据不区分整数和小数，数值型和字符型数据的区别是数值型数据不用引号括起来。例如：

```text
var num1 = 54;
var num2 = 5.4;
```

Number类型内置了一些方法，其中toString\(\) 方法返回指定 Number 对象的字符串表示形式。

```text
var count = 10;

print( count.toString() );   // 输出 "10"
print( (17).toString() );    // 输出 "17"

var x = 6;

print( x.toString(2) );      // 输出 "110"
print( (254).toString(16) ); // 输出 "fe"

print( (-10).toString(2) ); // 输出 "-1010"
print( (-0xff).toString() ); // 输出 "-11111111"
```

### String字符串 <a id="string&#x5B57;&#x7B26;&#x4E32;"></a>

字符串由多个字符构成，字符可以是字母、数字、标点符号或空格。字符串必须放在单引号或者双引号中。例如：

```text
var txt1 = "JavaScript";
```

### Symbol符号类型 <a id="symbol&#x7B26;&#x53F7;&#x7C7B;&#x578B;"></a>

符号类型在ECMAScript 第6版 中被引入Javascript。 符号类型是唯一的并且是不可修改的。

### Object对象类型 <a id="object&#x5BF9;&#x8C61;&#x7C7B;&#x578B;"></a>

在Javascript里，对象是非常重要的一种数据类型，对象可以被看作是由一些彼此相关的属性和方法集合在一起构成的数据实体。JavaScript中内置了一些对象，如array（数组）、date（日期）等等。

#### 数组 <a id="&#x6570;&#x7EC4;"></a>

字符串、数值型和布尔型变量在任意时刻只能存储一个值。如果要用一个变量存储多个值，就需要使用数组。数组是由名称相同的多个值构成的一个集合，集合中的值是数组的元素（element）。例如可以将一个班级的所有成员姓名存储在数组中。

在Javascript中，使用array关键字来定义数组，在定义中，可以声明数组的大小，也可以不声明数组中元素的个数。例如：

```text
var country = new array(180);   //定义了数组的大小
var mybooks = new array();      //没有定义数组的大小
mybooks[0] = “HTML”;          //为数组mybooks的第一个元素赋值
mybooks[1] = “JavaScript”;    //为数组mybooks的第二个元素赋值
```

数组中元素的索引默认从0开始，上例中的“mybooks\[0\]”表示数组中的第一个元素。

除了使用array关键字定义数组外，还可以直接使用方括号定义数组，数组中的元素要用逗号隔开，最后一个元素后没有逗号。如：

```text
var site = [”腾讯”,”新浪”,”搜狐”,”网易”];
```

### 查看变量类型 <a id="&#x67E5;&#x770B;&#x53D8;&#x91CF;&#x7C7B;&#x578B;"></a>

在JavaScript中，typeof操作符能返回一个字符串,表示未经求值的操作数\(unevaluated operand\)的类型。

```text
var a = 1;
alert(typeof a);
```

### 变量类型的转换 <a id="&#x53D8;&#x91CF;&#x7C7B;&#x578B;&#x7684;&#x8F6C;&#x6362;"></a>

JavaScript 是一种弱类型或者说动态语言。开发者不用提前声明变量的类型，在程序运行过程中，类型会被自动确定，这也意味着我们可以使用同一个变量保存不同类型的数据：

```text
var foo = 42;    // foo is a Number now
var foo = "bar"; // foo is a String now
var foo = true;  // foo is a Boolean now
```

除了让程序自动确定类型外，有时，我们也可以使用以下函数强制转换数据类型：

1. **Number\(\)** 强制内容转为数字；
2. **Boolean\(\)** 强制内容转为布尔值；
3. **String\(\)** 强制内容转为字符串；

如：

```text
var　t1　=　Boolean("");       //返回false,空字符串
var　t2　=　Boolean("s");  //返回true，非空字符串
```

> 2. symbol类型是ECMAScript6新增的数据类型，是一种唯一、不可变的变量。[ ↩](https://yangjh.gitee.io/front-end/js/jstype.html#reffn_2)

