# 文档元数据相关元素 {#文档元数据相关元素}

## head {#head}

`head`元素是`html`元素的第一个子元素，用来标记`HTML`文档的一系列元数据（如文档标题、作者、关键词、相关样式表、相关脚本等等）。

```php
<!DOCTYPE html>
<html>
 <head>
  <meta charset="utf-8">
 </head>
 <body>
 ...
```

## title {#title}

`title`元素位于`head`元素之中，用来标记整个HTML文档的标题或名称，`title`元素不得重复出现。

## base {#base}

`base`元素位于`head`元素之中，通过`href`属性设定文档基准URL、通过`target`属性设定文档中所有超级链接的默认打开方式。 如：

```php
<!DOCTYPE html>
<html>
    <head>
        <title>This is an example for the <base> element</title>
        <base href="http://www.example.com/news/index.html">
    </head>
    <body>
        <p>Visit the <a href="archives.html">archives</a>.</p>
    </body>
</html>
```

上例中`base`元素`href`的值必须为绝对地址。p元素中的超级链接最终实际地址为：

```
 "http://www.example.com/news/archives.html"
```

以下代码将使得网页中超级链接的打开方式设定为新建窗口打开：

```

```

上例中的第一个超级链接将在新建窗口打开，第二个超级链接将在自身窗口打开。

## link {#link}

`link`元素位于`head`元素中，用来连接和当前文档相关的外部资源。`link`元素必须指定`rel`属性。如：

```

```

## meta {#meta}

`meta`元素用来标记不能被`title、base、link、style和script`元素标记的其他各种元数据，如网页关键词、版权信息、页面编码信息等等，最常见的是通过`meta`元素设定页面的编码信息：

```

```

字符编码是一项极为复杂的主题，字符编码指示文件将显示什么字符，在选择一种字符编码之前，必须确保所使用的文本编辑器能够使用这种编码方式保存文档（Sunlime Text编辑器的默认编码方式就是UTF-8）。Unicode是一种表示所有字母和符号的可靠方式，Unicode目前支持超过99000个字符！

`meta`元素除了拥有全局性属性外，还可设定`name、http-equiv、content`值。

```

```

## style {#style}

`style`元素是`head`元素的子元素，用来设定HTML文档的内部样式表。

```

```



