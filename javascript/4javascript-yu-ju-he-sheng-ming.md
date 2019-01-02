# 4、JavaScript语句和声明

## 语句和声明 <a id="&#x8BED;&#x53E5;&#x548C;&#x58F0;&#x660E;"></a>

JavaScript 应用程序是由许多语法正确的语句组成的。单个语句可以跨多行。如果每个语句用分号隔开，那么多个语句可以在一行中出现。

### 控制流程 <a id="&#x63A7;&#x5236;&#x6D41;&#x7A0B;"></a>

#### 块声明 <a id="&#x5757;&#x58F0;&#x660E;"></a>

用于组合零个或多个语句。该块由一对大括号界定。

#### break <a id="break"></a>

break 语句中止当前循环，switch语句或label 语句，并把程序控制流转到紧接着被中止语句后面的语句。

#### continue <a id="continue"></a>

continue 语句结束当前（或标签）的循环语句的本次迭代，并继续执行循环的下一次迭代。

#### 空语句 <a id="&#x7A7A;&#x8BED;&#x53E5;"></a>

空语句是一个分号（;），表示不会执行任何语句，即使 JavaScript 语法需要一个语句。

#### if……else <a id="ifelse"></a>

根据设定条件，选择性地执行语句，当指定条件为true时会执行一条语句，如果该条件为false，则执行另一条语句。

```text
if (condition) {
   statements1
} else {
   statements2
}
```

#### switch <a id="switch"></a>

switch 语句对一个表达式求值，将结果与 case 子语句比较，如果匹配，则从 case 处的语句向下执行。

```text
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

#### throw <a id="throw"></a>

throw语句用来抛出一个用户自定义的异常。当前函数的执行将被停止（throw之后的语句将不会执行），并且控制将被传递到调用堆栈中的第一个catch块。如果调用者函数中没有catch块，程序将会终止。

```text
function getRectArea(width, height) {
  if (isNaN(width) || isNaN(height)) {
    throw "Parameter is not a number!";
  }
}

try {
  getRectArea(3, 'A');
}
catch(e) {
  console.log(e);
  // expected output: "Parameter is not a number!"
}
```

#### try...catch <a id="trycatch"></a>

try...catch语句将能引发错误的代码放在try块中，并且对应一个响应，然后有异常被抛出。语法如下：

```text
try {
   try_statements
}
[catch (exception_var_1 if condition_1) { // non-standard
   catch_statements_1
}]
...
[catch (exception_var_2) {
   catch_statements_2
}]
[finally {
   finally_statements
}]
```

### 声明 <a id="&#x58F0;&#x660E;"></a>

#### var <a id="var"></a>

声明一个变量，可同时初始化。变量声明，无论发生在何处，都在执行任何代码之前进行处理。用var声明的变量的作用域是它当前的执行上下文，它可以是嵌套的函数，也可以是声明在任何函数外的变量。建议始终声明变量，无论它们是在函数还是全局作用域内。 而在 ECMAScript 5 严格模式下，分配给未声明的变量会引发错误。通过var声明的变量没有块级作用域。

```text
ar x = 1;
{
    var x = 2;
    console.log(x); // 输出 2
}
console.log(x); // 输出 2
```

由于变量声明（以及其他声明）总是在任意代码执行之前处理的，所以在代码中的任意位置声明变量总是等效于在代码开头声明。这意味着变量可以在声明之前使用，这个行为叫做“hoisting”。“hoisting”就像是把所有的变量声明移动到函数或者全局代码的开头位置。

#### let <a id="let"></a>

let允许你声明一个作用域被限制在块级中的变量、语句或者表达式。

```text
function varTest() {
  var x = 1;
  if (true) {
    var x = 2;  // 同样的变量!
    console.log(x);  // 2
  }
  console.log(x);  // 2
}

function letTest() {
  let x = 1;
  if (true) {
    let x = 2;  // 不同的变量
    console.log(x);  // 2
  }
  console.log(x);  // 1
}
```

#### const <a id="const"></a>

声明一个只读的命名常量，此声明创建一个常量，其作用域可以是全局或本地声明的块。 与var变量不同，全局常量不会变为窗口对象的属性。必须在声明的同一语句中指定它的值，一个常量不能和它所在作用域内的其他变量或函数拥有相同的名称。

### 函数和类 <a id="&#x51FD;&#x6570;&#x548C;&#x7C7B;"></a>

#### function <a id="function"></a>

声明一个指定参数的函数。JavaScript 中的函数声明被提升到了函数定义。你可以在函数声明之前使用该函数。

```text
hoisted(); // "foo"

function hoisted() {
     console.log("foo");
}
```

#### function\* <a id="function"></a>

生成器函数使 iterators 更容易使用。

生成器函数在执行时能暂停，后面又能从暂停处继续执行。调用一个生成器函数并不会马上执行它里面的语句，而是返回一个这个生成器的 迭代器 （iterator ）对象。当这个迭代器的 next\(\) 方法被首次（后续）调用时，其内的语句会执行到第一个（后续）出现yield的位置为止，yield 后紧跟迭代器要返回的值。或者如果用的是 `yield*`（多了个星号），则表示将执行权移交给另一个生成器函数（当前生成器暂停执行）。

#### return <a id="return"></a>

指定函数的返回值。当在函数体中使用return语句时，函数将会停止执行。如果指定一个值，则这个值返回给函数调用者。默认情况下，函数是返回 undefined 的。想要返回一个其他的值，函数必须通过一个 return 语句指定返回值。

return语句也可以返回函数，即所谓闭包函数：

```text
function magic(x) {
  return function calc(x) { return x * 42};
}

var answer = magic();
answer(1337); // 56154
```

#### class <a id="class"></a>

class 声明创建一个基于原型继承的具有给定名称的新类。不同于类表达式，类声明不允许再次声明已经存在的类，否则将会抛出一个类型错误。

```text
class name [extends] {
  // class body
}
```

### 迭代器 <a id="&#x8FED;&#x4EE3;&#x5668;"></a>

#### do...while <a id="dowhile"></a>

创建一个循环来执行语句，直到该语句条件表达式的值为false。先执行语句，再执行条件表达式，该语句至少会执行一次。

```text
var result = '';
var i = 0;
do {
   i += 1;
   result += i + ' ';
} while (i < 5);
```

#### for <a id="for"></a>

创建一个由3个可选的表达式组成的循环，该循环用括号包裹，分号分割，并在循环体中执行语句。

```text
for (var i = 0; i < 9; i++) {
   console.log(i);
   // more statements
}
```

#### for each...in <a id="for-eachin"></a>

通过指定的变量迭代对象所有属性的值。针对每个唯一的属性，会执行指定的语句块。作为ECMA-357\(E4X\)标准的一部分,for each...in语句已被废弃,E4X中的大部分特性已被删除,但考虑到向后兼容,for each...in只会被禁用而不会被删除,可以使用ES6中新的for...of语句来代替

#### for...in <a id="forin"></a>

for...in 循环只遍历可枚举属性。循环将遍历对象本身的所有可枚举属性，以及对象从其构造函数原型中继承的属性（更接近原型链中对象的属性覆盖原型属性）。当迭代访问顺序很重要的数组时，最好用整数索引去进行for循环（或者使用 Array.prototype.forEach\(\) 或 for...of 循环）。

```text
var obj = {a:1, b:2, c:3};

for (var prop in obj) {
  console.log("obj." + prop + " = " + obj[prop]);
}
```

#### for...of <a id="forof"></a>

遍历可迭代的对象 \(包括arrays, 类数组对象, iterators and generators\)，对每个不同属性的属性，调用一个自定义的有执行语句的迭代钩子。

```text
let iterable = [10, 20, 30];

for (let value of iterable) {
    value += 1;
    console.log(value);
}
```

#### while <a id="while"></a>

创建一个循环语句，循环会一直持续到该语句条件表达式的值为false。先执行条件表达式，然后执行语句。

### 其他 <a id="&#x5176;&#x4ED6;"></a>

#### debugger <a id="debugger"></a>

debugger 语句调用任何可用的调试功能，例如设置断点。 如果没有调试功能可用，则此语句不起作用。

