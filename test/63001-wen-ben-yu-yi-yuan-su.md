# 6、文本语义元素

## a <a id="a"></a>

A 元素用来表示超链接或者文档内部锚点。如果a元素有href属性，它就表示超链接。

当a 元素表示超链接时，可以使用target属性指定链接打开方式，如：

```php
<a href="http://www.baidu.com" target="_blank">百度</a>
```

之前在\ref{sub:块元素与行内元素}我们提到，行内元素不能包含块元素，但是a元素是个例外，a元素内部可以是文字、图片等行内元素，也可以是段落、标题等块内容。

链接通常可以分为两类：指向本站内部的链接和指向外部站点的链接。这些链接通过a元素的href属性来指定。我们常使用相对路径来指定网站内部的链接，相对路径中不包含域名（如.com，.org， .edu，等等）信息，因为链接指向的网页位于同一站点，因此href属性的值只需要包含网页文件所在的路径和文件名即可，如:`<ahref="about.html">About</a>`；指向外部站点页面的链接必须使用绝对路径，绝对路径包含完整的URL信息。通常是以http开头，包含主机域名以及文件路径和文件名称。如`<ahref="http://www.google.com/">Google</a>`

a元素还可以通过在href属性中添加`#`创建指向文档内部具体位置的超级链接，如：

```php
<body id="top">
  ...
  <a href="#top">Back to top</a>
  ...
</body>
```

上述代码将创建一个返回到body开始位置的超级链接，实现返回到页首的效果。

## em <a id="em"></a>

Em 元素表示对其标记内容的强调，在语义上强调与其他内容的不同。

## strong <a id="strong"></a>

Strong元素用来表示其标记内容非常重要、非常紧急，在语义上表示重要性。

## small <a id="small"></a>

Small 元素表示诸如注释、说明等等不同于正文的内容。

```php
<dl>
<dt>标准间</dt>
<dd>199元。<small>不含早餐</small></dd>
<dd>229元。<small>含双早</small></dd>
</dl>
```

## s <a id="s"></a>

S 元素用来标记不再准确或者已不相关的内容。

```php
<dl>
<dt>标准间</dt>
<dd><s>199元。<small>不含早餐</small></s></dd>
<dd>189元。<small>含早餐</small></dd>
</dl>
```

## cite <a id="cite"></a>

Cite用来表示对作品（如书籍、电影、歌曲、新闻等等）的引用，cite中的内容必须包含作品名称或者作者名称或者URL地址。

```php
<cite>
    <a href="http://world.people.com.cn/n1/2016/0106/c1002-28019941.html">聚焦朝鲜的历次核试验</a>. 人民网. 
</cite>
```

## q <a id="q"></a>

Q 元素表示对外部资料的直接引用。

```php
<p>那个男人说<q>事情不能再拖了</q>。我也赞同他的观点。</p>
```

可以使用cite属性来指定外部资料的来源，如：

```php
<p>
    万维网联盟在其 <cite>About W3C</cite> 页面中表明，它的使命是 
    <q cite="http://www.w3.org/Consortium/">通过制定协议和规范，引导万维网发挥其全部潜力，确保万维网的长期发展。</q>. 
</p>
```

## dfn <a id="dfn"></a>

dfn元素用来表示术语的定义。如：

```text
<
p
>
doit.im是一款
<
dfn
>
<
abbr
title
=
"
Get Thing Done
"
>
GTD
<
/
abbr
>
<
/
dfn
>
软件，用来帮助用户进行任务管理。
<
/
p
>
```

## abbr <a id="abbr"></a>

Abbr 元素表示某个术语的缩写。使用title属性来指定术语的全部名称。

## data <a id="data"></a>

Data 元素用来标记数据。

## time <a id="time"></a>

Time 元素用来标记时间。

## code <a id="code"></a>

Code 元素用来标记代码。

## var <a id="var"></a>

Var 元素用来标记变量。

## samp <a id="samp"></a>

Samp 元素用来标记程序或者计算机的输出结果。

## kbd <a id="kbd"></a>

Kbd 元素用来标记用户输入的内容，尤其是键盘输入。

```text
使用快捷键
<
kbd
>
Ctrl + S 
<
/
kdb
>
保存文档。
```

## sub和sup <a id="sub&#x548C;sup"></a>

Sub 表示下标，sup表示上标。

## i <a id="i"></a>

I 元素表示不同于正文的可替换声音、情绪或其他语言的内容等等。

## b <a id="b"></a>

B 元素用来表示诸如关键字、产品名称等等需要引起注意的内容。

## u <a id="u"></a>

U 元素用来标记不能非常清楚表达的内容，如汉语诗歌等。

## mark <a id="mark"></a>

Mark 元素用来标记高亮内容，以表示其与其他内容的区别。

## ruby <a id="ruby"></a>

Ruby 元素用来为东亚字符添加注音。

## span <a id="span"></a>

Span 元素用来在逻辑结构上对文本内容进行区分，比如在新闻信息中，我们可以将日期、作者信息、消息来源等内容，用span元素加以标记，结合class属性，进行文本区分。

## br <a id="br"></a>

Br 元素表示另起一行

