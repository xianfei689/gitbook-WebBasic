# 5、内容组织元素

合理使用内容组织元素，能帮助浏览器等设备更好地理解网页的内容。

## 内容组织相关元素 <a id="&#x5185;&#x5BB9;&#x7EC4;&#x7EC7;&#x76F8;&#x5173;&#x5143;&#x7D20;"></a>

### p <a id="p"></a>

`p`元素用来表示段落，列表元素`ol`和`ul`不能包含于`p`元素中。

### address <a id="address"></a>

address元素用来表示联系方式。

```php
<footer>
 <address>
  要了解更多信息，请联系<a href="mailto:js@example.com">作者</a>.
 </address>
 <p><small>© copyright 2038 Example Corp.</small></p>
</footer>
```

### hr <a id="hr"></a>

`hr`元素表示段落级别的语义中断，例如，一个故事中的场景切换，或者文章中的主题切换。

### pre <a id="pre"></a>

`Pre`元素表示预定义格式的文本块，常用来标记诗歌、代码等等内容。

### blockquote <a id="blockquote"></a>

`Blockquote`元素表示从别处引用的内容。

### ol <a id="ol"></a>

`Ol`元素表示一组有序列表，所谓有序列表，就是列表项目的顺序是有意义的，如菜谱中的工序。列表项目使用`li`元素标记。

### ul <a id="ul"></a>

`Ul`元素表示一组无序列表，所谓无序，就是列表的顺序可以随意改变，列表项目使用li元素标记。

### li <a id="li"></a>

`Li`元素表示列表中的项目。

### dl <a id="dl"></a>

`Dl`元素表示一组包含“名称-值”的自定义列表，其中名称使用`dt`标记，值可以是一个或者多个`dd`元素。

```php
<dl>
 <dt> 作者 </dt>
 <dd> Adam </dd>
 <dd> Cui </dd>
 <dt> 编辑 </dt>
 <dd> Fang </dd>
</dl>
```

### dt <a id="dt"></a>

`Dt`元素用来表示自定义列表dl中的名称、术语。

### dd <a id="dd"></a>

`Dd`元素用来表示自定义列表`dl`中名称`dt`的解释、定义或者值。

### figure <a id="figure"></a>

`Figure`元素用来表示对插图、图表、照片、代码块等内容的引用。

```php
<figure>
 <img src="bubbles-work.jpeg">
 <figcaption>图片标题</figcaption>
</figure>
```

### figcaption <a id="figcaption"></a>

`Figcaption`元素用来表示`figure`元素中的标题。

### main <a id="main"></a>

`Main`元素表示文档或者应用的最重要或者核心部分。`main`元素可与`header、footer`一起标记网页的内容。

`main`元素不要放在`article、 aside、 footer、 header、或者 nav`元素中。

```php
<!DOCTYPE html>
  <html>
  <head>
    <title>………………</title>
  </head>
  <body>

  <header>
  <nav>
  <ul>
  <li>……</li>
  <li>……</li>
  <li>……</li>
  </ul>
  </nav>
  </header>

  <main>
  …………
  …………
  …………
  </main>

  <footer>…………</footer>

  </body>
  </html>
```

### div <a id="div"></a>

`Div`元素本身并没有特殊含义，它是HTML中用来标记内容结构的最常用元素，用来将相关的元素组织在一起，形成逻辑上的整体。

