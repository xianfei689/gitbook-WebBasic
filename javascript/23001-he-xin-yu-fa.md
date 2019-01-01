# JavaScript核心语法 {#javascript核心语法}

## 注释 {#注释}

JavaScript的注释和CSS注释类似，分多行和单行，多行注释使用`/* ... */`，如：

```
/*
Everything in between is a comment.
*/
```

单行注释使用“`//`”表示，如：

```
// This is a comment
```

## 变量 {#变量}

所谓变量就是程序中数据的临时存放场所。JavaScript的变量定义都是使用“var”关键字，示例如下：

```
var author = "yangjh";
var age = 35;
var Age = 36;
var male = true;
var a,b,c;
```

上述三行代码中，var关键字表示声明变量，变量名紧跟其后，通过等于号将变量赋予变量初始值。每一行结束的分号可以不写，但书写分号后，能增强代码的可读性，加不加分号取决于个人选择。

变量的名称必须遵循以下规则：

1. 首字符必须是字母、下划线或美元符号。
2. 其余字母可以是下划线、美元符号、任意字母或者数字。
3. 变量名称不能是关键字或保留字。
4. 变量名对大小写敏感，例如：变量age和Age是不同的变量。
5. 变量名中不能有空格、回车符或其他标点字符。

## 分号 {#分号}

JavaScript行末可以不加分号，建议能不加分号就不加，那在什么时候需要加分号呢？真正会导致上下行解析出问题的 token 有 5 个：括号，方括号，正则开头的斜杠，加号，减号。实际代码中用正则、加号、减号作为行首的情况几乎没有，所以总结下来就是一句话：**一行开头是括号或者方括号的时候加上分号就可以了，其他时候全部不需要。**例如：

```
const a = 2;
[ 3, 4 ].forEach(n => console.log(n))
a = b;
(function(){
...
})();
```

上述代码第一行末如果不加分号，则会报错，第三行如果不加分号，就会被编译器解释`a = b(function(){...})()`，这和加了分号的语义是不一致的。

## 常量 {#常量}

常量意味着其中保存的值是固定不变的，JavaScript使用关键字const声明常量，习惯上，常量名称使用大写字母。

```
const A = 7;
console.log("A is " + A + ".");
```

上面的例子将输出 "A is 7."。

## 运算符 {#运算符}

运算符用于将一个或多个值运算成结果。在Javascript中，常用的运算符有以下几种类别：

### 算术运算符 {#算术运算符}

算术运算符能对操作数进行运算，返回一个数值型的值。常见的有`+、-、 *、/`。

### 关系运算符 {#关系运算符}

关系运算符通常用于检查两个操作数之间的关系，返回值为true或false。

| 运算符 | 说明 | 例子 | 结果 |
| :--- | :--- | :--- | :--- |
| == | 是否相等 | 5=="5" | TRUE |
| === | 是否全等 | 5=="5" | FALSE |
| ！= | 是否不等 | 5！="5" | FALSE |
| !== | 是否不全等 | 5！="5" | TRUE |
| &gt; | 是否大于 | 5&gt;8 | FALSE |
| &lt; | 是否小于 | 5&lt;8 | TRUE |
| &gt;= | 是否大于等于 | 5&gt;=8 | FALSE |
| &lt;= | 是否小于等于 | 5&lt;=8 | TRUE |

### 赋值运算符 {#赋值运算符}

赋值运算符是使用最多的运算符，常见的赋值运算符就是“=”，它将右边的值赋与等号左边的变量。

### 逻辑运算符 {#逻辑运算符}

逻辑运算符用来判断操作数之间的逻辑关系，返回值为true和false。javascript支持一下三种逻辑运算符。

| 运算符 | 说明 | 例子 | 结果 |
| :--- | :--- | :--- | :--- |
| && | 逻辑与 | 5&gt;3 && 4&gt;3 | TRUE |
| \|\| | 逻辑或 | 5&gt;3 \|\| 3&gt;5 | FALSE |
| ! | 逻辑非 | !\(3&gt;5\) | TRUE |

### 连接运算符 {#连接运算符}

连接运算符“+”能将字符串连接起来构成一个新的字符串。如：

```
var txt1 = "JavaScript"；
var txt2 = "基础教程";
var txt3 = txt1 + txt2;
```

变量txt3的结果是“JavaScript基础教程”。

## 流程控制 {#流程控制}

和其他语言一样，JavaScript也是由上到下逐行执行代码，还可以通过分支、循环改变执行流程。

### 语句块 {#语句块}

语句块用来组织多条语句。用一对花括号界定语句块。语法如下：

```
{
  statement_1;
  statement_2;
  ...
  statement_n;
}
```

注意语句块不是以分号结尾。语句块常在流程控制语句中使用。

### break {#break}

break 语句中止当前循环，switch语句或label 语句，并把程序控制流转到紧接着被中止语句后面的语句。

```
function testBreak(x) {
  var i = 0;

  while (i < 6) {
    if (i == 3) {
      break;
    }
    i += 1;
  }

  return i * x;
}
```

### if...else {#ifelse}

根据设定条件，选择性地执行语句，当指定条件为true时会执行一条语句，如果该条件为false，则执行另一条语句。

```
if (condition) {
   statements1
} else {
   statements2
}
```

### switch {#switch}

switch 语句对一个表达式求值，将结果与 case 子语句比较，如果匹配，则从 case 处的语句向下执行。

```
switch (expression) {
  case value1:
    // 当 expression 的结果与 value1 匹配时，从此处开始执行
    statements1；
    [break;]
  case value2:
    // 当 expression 的结果与 value2 匹配时，从此处开始执行
    statements2;
    [break;]
  ...
  case valueN:
    // 当 expression 的结果与 valueN 匹配时，从此处开始执行
    statementsN;
    [break;]
  default:
    // 如果 expression 与上面的 value 值都不匹配时，执行此处的语句
    statements_def;
    [break;]
}
```

switch语句中的break语句，能保证程序执行到该语句时，不再执行后续语句，而是跳出switch语句块。

### for {#for}

for语句创建一个包含初始条件、终止条件和步进规则的循环体。例如下面的代码将循环10次（从0-9），然后在控制台中打印出0-9的数字：

```
for (var i = 0; i < 9; i++) {
   console.log(i);
   // more statements
}
```

### while {#while}

while 语句可以在某个条件表达式为真的前提下，循环执行指定的一段代码，直到那个表达式不为真时结束循环。语法如下：

```
while (condition) {
  statement
}
```

### do...while {#dowhile}

do...while 语句创建了一个循环，该循环执行一个指定的语句直到condition 的值为 false。 condition 在执行statement后才会被赋值，statement至少执行一次。语法如下：

```
do {
   statement;
   ...
 }
while (condition);
```

## 函数 {#函数}

使用关键字function声明一个函数。函数还可有参数和返回值。

```
function name([param,[, param,[..., param]]]) {
   [statements]
}
```

参数可以是常量、变量或表达式，多个参数之间用逗号隔开。若函数需要返回值，使用return语句。默认情况下，函数是返回 undefined 类型。想要返回一个其他的值，函数必须通过一个 return 语句指定返回值。

定义函数的时候，并不会执行构成该函数的任何语句。只有当调用该函数时，函数里面的语句才会执行，直到碰到return语句，return语句之后的内容不会被执行。

### 回调函数 {#回调函数}

在JavaScript中，回调函数具体的定义为：函数A作为参数\(函数引用\)传递到另一个函数B中，并且这个函数B执行函数A。我们就说函数A叫做回调函数。如果没有名称\(函数表达式\)，就叫做匿名回调函数。例如：

```js
// 当参数a大于10且参数func2是一个方法时 执行func2
function func1(a, func2) {
    if (a > 10 && typeof func2 == 'function') {
        func2()
    }
}
func1(11, function() {
    console.log('this is a callback')
})
```

通常情况下，回调函数当func1执行到某一步或者满足某种条件的时候才执行传入的参数func2。

回调函数不是由该函数的实现方直接调用，而是在特定的事件或条件发生时由另外的一方调用的，用于对该事件或条件进行响应。因此，回调本质上是一种设计模式，jQuery\(包括其他框架\)的设计原则遵循了这个模式。

