## XHTML 是什么？

* XHTML 指可扩展超文本标签语言（EXtensible HyperText Markup Language）。

* XHTML 的目标是取代 HTML。

* XHTML 与 HTML 4.01 几乎是相同的。

* XHTML 是更严格更纯净的 HTML 版本。

* XHTML 是作为一种 XML 应用被重新定义的 HTML。

* XHTML 是一个 W3C 标准。

## 为什么要使用XHTML？

我们认为万维网上的许多页面都包含着糟糕的 HTML 代码。

下面的 HTML 代码仍然可以工作得很好，即使它没有遵守 HTML 规则：

```html
<html>
<head>
<title>This is bad HTML</title>
<body>
<h1>Bad HTML
</body>
```

XML 是一种标记化语言，其中所有的东西都要被正确的标记，以产生形式良好的文档。

XML 用来描述数据，而 HTML 则用来显示数据。

HTML 和 XML 各自的长处加以结合，我们得到了在现在和未来都能派上用场的标记语言 - XHTML。

## XHMTL vs HTML

### 最主要的不同：

* XHTML 元素必须被正确地嵌套。
* XHTML 元素必须被关闭。
* 标签名必须用小写字母。
* XHTML 文档必须拥有根元素。

## 语法

---

## 更多的 XHTML 语法规则：

* 属性名称必须小写
* 属性值必须加引号
* 属性不能简写
* 用 Id 属性代替 name 属性
* XHTML DTD 定义了强制使用的 HTML 元素

## 属性名称必须小写

这是错误的：

```php
<table WIDTH="100%">
```

这是正确的：

```php
<table width="100%">
```

## 属性值必须加引号

这是错误的：

```php
<table width=100%>
```

这是正确的：

```php
<table width="100%">
```

## 属性不能简写

这是错误的：

```php
<input checked>
<input readonly>
<input disabled>
<option selected>
<frame noresize>
```

这是正确的：

```php
<input checked="checked" />
<input readonly="readonly" />
<input disabled="disabled" />
<option selected="selected" />
<frame noresize="noresize" />
>
```

下面是一个 HTML 的简写属性列表，以及在 XHTML 中的改写：

| HTML | XHTML |
| :--- | :--- |
| compact | compact="compact" |
| checked | checked="checked" |
| declare | declare="declare" |
| readonly | readonly="readonly" |
| disabled | disabled="disabled" |
| selected | selected="selected" |
| defer | defer="defer" |
| ismap | ismap="ismap" |
| nohref | nohref="nohref" |
| noshade | noshade="noshade" |
| nowrap | nowrap="nowrap" |
| multiple | multiple="multiple" |
| noresize | noresize="noresize" |

## 用 id 属性代替 name 属性

HTML 4.01 针对下列元素定义 name 属性：a, applet, frame, iframe, img, 和map。

在 XHTML 中不鼓励使用 name 属性，应该使用 id 取而代之。

这是错误的：

```php
<img src="picture.gif" name="picture1" />
```

这是正确的：

```php
<img src="picture.gif" id="picture1" />
```

### 重要的兼容性提示：

你应该在 "/" 符号前添加一个额外的空格，以使你的 XHTML 与当今的浏览器相兼容。

## 语言属性（lang）

lang 属性应用于几乎所有的 XHTML 元素。它定义元素内部的内容的所用语言的类型。

如果在某元素中使用 lang 属性，就必须添加额外的 xml:lang，像这样：

```php
<div lang="no" xml:lang="no">Heia Norge!</div>
```

## 强制使用的 XHTML 元素

所有 XHTML 文档必须进行文件类型声明（DOCTYPE declaration）。在 XHTML 文档中必须存在html、head、body元素，而 title 元素必须位于在 head 元素中。

下面是一个最小化的 XHTML 文件模板：

```php
<!DOCTYPE Doctype goes here>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Title goes here</title>
</head>

<body>
</body>

</html>
```

提示：文件类型声明并非 XHTML 文档自身的组成部分。它并不是 XHTML 元素，也没有关闭标签。

提示：在 XHTML 中，&lt;html&gt; 标签内的 xmlns 属性是必需的。然而，即使当 XHTML 文档中没有这个属性时，w3.org 的验证工具也不会提示错误。这是因为，"xmlns=[http://www.w3.org/1999/xhtml](http://www.w3.org/1999/xhtml)" 是一个固定的值，即使你没有把它包含在代码中，这个值也会被添加到 &lt;html&gt; 标签中。

