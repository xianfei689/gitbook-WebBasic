# XHTML DTD

---

**XHTML 定义了三种文件类型声明。**

**使用最普遍的是 XHTML Transitional。**

## &lt;!DOCTYPE&gt; 是强制使用的。

一个 XHTML 文档有三个主要的部分：

* DOCTYPE
* Head
* Body

基本的文档结构是这样的：

```php
<!DOCTYPE ...>
<html>
<head>
<title>... </title>
</head>
<body> ... </body>
</html>
```

## 一个 XHTML 的实例

这个一个简单的（最小化的） XHTML 文档：

```php
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>simple document</title>
</head>
<body>
<p>a simple paragraph</p>
</body>
</html>
```

文档类型声明定义文档的类型：

```php
<!DOCTYPE html
PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
```

文档的其余部分类似 HTML：

```
<html>
<head>
<title>simple document</title>
</head>
<body>
<p>a simple paragraph</p>
</body>
</html>
```



