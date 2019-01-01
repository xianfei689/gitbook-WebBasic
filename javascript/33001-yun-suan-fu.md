# Javascript中的表达式和运算符 {#javascript中的表达式和运算符}

表达式和运算符是编程语言的基本规则，必须熟练掌握。以下是JavaScript语言的全部（除废弃之外）的表达式和运算符：

## 主要表达式 {#主要表达式}

首先，我们看 JavaScript 中基本关键字和常用表达式：

### `this` {#this}

`this`关键字指向函数的执行上下文。函数的`this`关键字在 JavaScript 中的表现略有不同，此外，在严格模式和非严格模式之间也会有一些差别。在绝大多数情况下，函数的调用方式决定了`this`的值。`this`不能在执行期间被赋值，并且在每次函数被调用时this的值也可能会不同。

#### 全局语境中的this {#全局语境中的this}

在全局执行上下文中（在任何函数体外部）this 都指代全局对象。

```
<script>
"use strice";
console.log(this);
console.log(this === window);
</script>
```

#### 函数语境中的this {#函数语境中的this}

在函数内部，this的值取决于函数被调用的方式。在严格模式下，this将保持他进入执行上下文时的值，所以下面的this将会默认为undefined。

```
<script>
function f1() {
    return this;
}

function f2() {
    "use strict"; // 这里是严格模式
    return this;
}
console.log(f1());
console.log(f2());
console.log(window.f2());
</script>
```

### function {#function}

function 关键字定义了函数表达式。使用表达式方式定义函数的语法如下：

```
let function_expression = function [name]([param1[, param2[, ..., paramN]]]) {
   statements
};
```

使用表达式创建的函数，不能在创建之前调用。

### class {#class}

class 关键字定义了类表达式。

```
const MyClass = class [className] [extends] {
  // class body
};
```

和函数表达式相同的一点是，类表达式可以是命名也可以是匿名的。如果是命名类表达式，这个名字只能在类体内部才能访问到。

```
const Foo = class NamedFoo {
  constructor() {}
  whoIsThere() {
    return NamedFoo.name;
  }
}

let bar = new Foo();

bar.whoIsThere();
// "NamedFoo"

NamedFoo.name;
// ReferenceError: NamedFoo is not defined

Foo.name;
// "NamedFoo"
```

### function\* {#function}

function\* 关键字在表达式内部定义一个生成器函数。

```
function* [name]([param1[, param2[, ..., paramN]]]) {
   statements
}
```

它返回一个 Generator 对象，并且它符合可迭代协议和迭代器协议。该对象有三个方法：

1. Generator.prototype.next\(\) 返回一个由 yield表达式生成的值。
2. Generator.prototype.return\(\) 返回给定的值并结束生成器。
3. Generator.prototype.throw\(\) 向生成器抛出一个错误。

### yield {#yield}

暂停和恢复一个生成器函数。yield关键字使生成器函数执行暂停，yield关键字后面的表达式的值返回给生成器的调用者。它可以被认为是一个基于生成器的版本的return关键字。示例如下：

```
function* countAppleSales () {
  var saleList = [3, 7, 5];
  for (var i = 0; i < saleList.length; i++) {
    yield saleList[i];
  }
}

var appleStore = countAppleSales(); // Generator { }
console.log(appleStore.next()); // { value: 3, done: false }
console.log(appleStore.next()); // { value: 7, done: false }
console.log(appleStore.next()); // { value: 5, done: false }
console.log(appleStore.next()); // { value: undefined, done: true }
```

### yield\* {#yield}

委派给另外一个generator函数或可迭代的对象。示例如下：

```
function* g1() {
  yield 2;
  yield 3;
  yield 4;
}

function* g2() {
  yield 1;
  yield* g1();
  yield 5;
}

var iterator = g2();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: 4, done: false }
console.log(iterator.next()); // { value: 5, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

### async function\* {#async-function}

async function 定义一个异步函数表达式。

### await {#await}

暂停或恢复执行异步函数，并等待promise的resolve/reject回调。

### \[\]

数组初始化/字面量语法。

```
var fruits = ['Apple', 'Banana'];

console.log(fruits.length);
// 2
通过索引访问数组元素

var first = fruits[0];
// Apple

var last = fruits[fruits.length - 1];
// Banana
```

### {}

对象初始化/字面量语法。一个对象初始化器，由花括号/大括号 \({}\) 包含的一个由零个或多个对象属性名和其关联值组成的一个逗号分隔的列表构成。

```
var o = {};
var o = {a: 'foo', b: 42, c: {}};

var a = 'foo', b = 42, c = {};
var o = {a: a, b: b, c: c};

var o = {
  property: function ([parameters]) {},
  get property() {},
  set property(value) {}
};
```

### /ab+c/i {#abci}

正则表达式字面量语法。

### \( \)

分组操作符。圆括号运算符由一对圆括号组成，包裹表达式和子表达式用来覆盖常规的，运算符优先级 ，达到低优先级的表达式比高优先级的表达式更早运算。

```
var a = 1;
var b = 2;
var c = 3;

a + b * c     // 7
a + (b * c)   // 7
(a + b) * c   // 9
```

## 左表达式 {#左表达式}

左边的值是赋值的目标。

### 属性访问符 {#属性访问符}

成员运算符提供了对对象的属性或方法的访问 \(object.property 和 object\["property"\]\).

### new {#new}

new 运算符创建了构造函数实例。

### new.target {#newtarget}

在构造器中，new.target 指向new调用的构造器。

### super {#super}

super 关键字调用父类的构造器.

### ...obj {#obj}

展开运算符可以将一个可迭代的对象在函数调用的位置展开成为多个参数,或者在数组字面量中展开成多个数组元素。

## 自增和自减 {#自增和自减}

| 运算符 | 意义 |
| :--- | :--- |
| A++ | 后置自增运算符 |
| A-- | 后置自减运算符 |
| ++A | 前置自增运算符 |
| A++ | 前置自减运算符 |

## 一元运算符 {#一元运算符}

| 运算符 | 意义 |
| :--- | :--- |
| delete | delete 运算符用来删除对象的属性 |
| void | void 运算符表示表达式放弃返回值 |
| typeof | typeof 运算符用来判断给定对象的类型. |
| + | 一元加运算符将操作转换为Number类型. |
| - | 一元减运算符将操作转换为Number类型并取反. |
| ~ | 按位非运算符. |
| ! | 逻辑非运算符. |

### 一元正号 {#一元正号}

一元正号运算符位于其操作数前面，计算其操作数的数值，如果操作数不是一个数值，会尝试将其转换成一个数值。 尽管一元负号也能转换非数值类型，但是一元正号是转换其他对象到数值的最快方法，也是最推荐的做法，因为它不会对数值执行任何多余操作。它可以将字符串转换成整数和浮点数形式，也可以转换非字符串值 true，false 和 null。小数和十六进制格式字符串也可以转换成数值。负数形式字符串也可以转换成数值（对于十六进制不适用）。如果它不能解析一个值，则计算结果为 NaN.

```
+3     // 3
+"3"   // 3
+true  // 1
+false // 0
+null  // 0
+function(val){ return val;} //NaN
```

## 算术运算符 {#算术运算符}

算术运算符能对操作数进行运算，返回一个数值型的值。常见的有`+、-、 *、/、%`。

## 关系运算符 {#关系运算符}

关系运算符通常用于检查两个操作数之间的关系，返回值为true或false。

| 运算符 | 说明 | 例子 | 结果 |
| :--- | :--- | :--- | :--- |
| in | 如果指定的属性在指定的对象或其原型链中，则in 运算符返回true。 | "PI" in Math | TRUE |
| instanceof | instanceof 运算符用来检测 constructor.prototype 是否存在于参数 object 的原型链上。 |  |  |
| &gt; | 是否大于 | 5&gt;8 | FALSE |
| &lt; | 是否小于 | 5&lt;8 | TRUE |
| &gt;= | 是否大于等于 | 5&gt;=8 | FALSE |
| &lt;= | 是否小于等于 | 5&lt;=8 | TRUE |

## 相等运算符 {#相等运算符}

如果相等，操作符返回的是Boolean\(布尔\)类型的true，否则是false。

| 运算符 | 说明 | 例子 | 结果 |
| :--- | :--- | :--- | :--- |
| == | 是否相等 | 5=="5" | TRUE |
| === | 是否全等 | 5=="5" | FALSE |
| ！= | 是否不等 | 5！="5" | FALSE |
| !== | 是否不全等 | 5！="5" | TRUE |

## 位移运算符 {#位移运算符}

在二进制的基础上对数字进行移动操作。

| 运算符 | 意义 |
| :--- | :--- |
| &lt;&lt; | 按位左移运算符。 |
| &gt;&gt; | 按位右移运算符。 |
| &gt;&gt;&gt; | 按位无符号右移运算符。 |

## 二进制位运算符 {#二进制位运算符}

| 运算符 | 意义 |
| :--- | :--- |
| & | 二进制位与（AND）。 |
| \| | 二进制位或（OR）。 |
| ^ | 二进制位异或（XOR）。 |

## 二元逻辑运算符 {#二元逻辑运算符}

逻辑运算符用来判断操作数之间的逻辑关系，返回值为true和false。javascript支持一下三种逻辑运算符。

| 运算符 | 说明 | 例子 | 结果 |
| :--- | :--- | :--- | :--- |
| && | 逻辑与 | 5&gt;3 && 4&gt;3 | TRUE |
| \|\| | 逻辑或 | 5&gt;3 \|\| 3&gt;5 | FALSE |
| ! | 逻辑非 | !\(3&gt;5\) | TRUE |

## 条件\(三元\)运算符 {#条件三元运算符}

`(condition ? ifTrue : ifFalse)`条件元素运算符把两个结果中其中一个符合运算逻辑的值返回。

## 赋值运算符 {#赋值运算符}

赋值运算符是使用最多的运算符，常见的赋值运算符就是“=”，它将右边的值赋与等号左边的变量。

## 逗号操作符 {#逗号操作符}

当你想要在期望一个表达式的位置包含多个表达式时，可以使用逗号操作符。这个操作符最常用的一种情况是：for 循环中提供多个参数。

  


