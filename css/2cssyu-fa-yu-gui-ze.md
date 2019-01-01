# CSS语法与规则 {#css语法与规则}

## 语法声明 {#语法声明}

CSS 由一系列声明构成。语法声明分成两类：at规则\(at-rules\)和CSS规则集\(rule sets\)。[\[11\]](https://yangjh.gitee.io/front-end/References.html#cite-11)声明之间可由空白字符连接。

### at 规则 {#at-规则}

At 规则以“@”关键字开始，之后紧跟标志符。比如：“@import”。

“@import” 规则的作用是从其他样式表文件中导入样式格式。@import 关键字之后必须跟随要引入到当前文件中的样式表URI地址，不过也可以仅用字符串表示。例如：

```css
@import "mystyle.css";
```

上述语法声明等同于：

```css
@import url("mystyle.css");
```

都表示要引用mystle.css样式表。

注意：“@import”不能放在语法块中，也不能放在“@charset” 或者“@import”规则之后。例如：

```
@import
"subs.css"
;
h1
{
color
:
 blue 
}
@import
"list.css"
;
```

上述代码中最后的@import语句将被忽略。

除了“@import”之外，常用的@规则还有“@media”，“@media”表示为特定媒体（多个媒体之间可用逗号分隔）声明样式，例如：

```
@media
 print
{
body
{
font-size
:
 10pt 
}
}
```

表示当页面打印时字体为10pt。

CSS支持的媒体类型有：

1. **all**
   适合所有设备。
2. **braille**
   适合布莱叶盲文触摸设备。
3. **embossed**
   适合布莱叶盲文打印设备。
4. **handheld**
   适合小屏幕、带宽有限的手持设备。
5. **print**
   适合打印设备。
6. **projection**
   适合投影仪。
7. **screen**
   适合计算机显示屏幕。
8. **speech**
   适合语音阅读设备。
9. **tv**
   适合早期低分辨率的电视。

### 规则集 {#规则集}

规则集，也称规则，由选择符和跟随其后的声明块组成。声明块以“{”开始，以“}”结束，其中的声明以“;”分隔。声明由属性名称和属性值组成，属性名称和属性值之间用“:”连接。例如：

```
h1
{
color
:
 red
;
}
p
{
color
:
 blue
;
}
em em
{
font-style
:
 normal
;
}
```

## CSS注释 {#css注释}

在CSS中，注释以“`/*`”开始，以“`*/`”结束，注释之内的内容会被浏览器忽略。注释不能嵌套使用。

