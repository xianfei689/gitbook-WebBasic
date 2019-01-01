# 区块元素 {#区块元素}

## 块元素与行内元素 {#块元素与行内元素}

绝大多数HTML元素是块元素（Block-level element）或者行内元素（Inline-level element）。这两者之间有什么不同？

块元素开始于新的一行，占据指定的宽度。块元素还可以嵌套块元素，还可以在内部使用行内元素。最常见的块元素就是段落`<p>、<div>`等等。

行内元素并不会开始于新的一行。它们按照字符的顺序依次再文档中显示，如从左到右，一个挨着一个，填满所在容器的宽度后才会换行。行内元素也可以嵌套使用，但是行内元素内部不能包含块元素。常见的行内元素有`<a>、<img>`等等。

## 区块元素 {#区块元素}

### body {#body}

Body元素用来标记全部文档内容。在HTML文档中，应该只能有一个body元素。

body元素属于`Sectioning root`类型的元素，即它可以包含其他区块元素。

### article {#article}

article元素表示网页中完整的信息，比如论坛中的帖子、报纸中的报道、博客文章、用户评论或者其他独立完整的内容。

```php
<article>
 <header>
  <h2>文章标题</h2>
  <p>发表时间 评论数</p>
 </header>
 <p>内容段落</p>
 <p>内容段落</p>
 <p>内容段落</p>
</article>
```

article元素属于`Sectioning content`类型。

### section {#section}

section元素表示文档或者应用中一般意义上的分区，比如二级标题及段落的组合，就是一个分区。

```php
<article class="book">
  <header>
    <h2>My Book</h2>
    <p>A sample with not much content</p>
    <p><small>Published by Dummy Publicorp Ltd.</small></p>
  </header>

  <section class="chapter">
    <h3>My First Chapter</h3>
    <p>This is the first of my chapters. It doesn’t say much.</p>
    <p>But it has two paragraphs!</p>
  </section>
  <section class="chapter">
    <h3>It Continues: The Second Chapter</h3>
    <p>Bla dee bla, dee bla dee bla. Boom.</p>
  </section>
  <section class="chapter">
    <h3>Chapter Three: A Further Example</h3>
    <p>It’s not like a battle between brightness and earthtones would go
    unnoticed.</p>
    <p>But it might ruin my story.</p>
  </section>
  <section class="appendix">
    <h3>Appendix A: Overview of Examples</h3>
    <p>These are demonstrations.</p>
  </section>
  <section class="appendix">
    <h3>Appendix B: Some Closing Remarks</h3>
    <p>Hopefully this long example shows that you <em>can</em> style
    sections, so long as they are used to indicate actual sections.</p>
  </section>
</article>
```

section元素也属于`Sectioning content`类型。

### nav {#nav}

nav元素用来表示一组连接到外部网页的链接，即导航条。

```
<
nav
>
<
h1
>
Navigation
<
/
h1
>
<
ul
>
<
li
>
<
a
href
=
"
articles.html
"
>
Index of all articles
<
/
a
>
<
/
li
>
<
li
>
<
a
href
=
"
today.html
"
>
Things sheeple need to wake up for today
<
/
a
>
<
/
li
>
<
li
>
<
a
href
=
"
successes.html
"
>
Sheeple we have managed to wake
<
/
a
>
<
/
li
>
<
/
ul
>
<
/
nav
>
```

nav元素属于`Sectioning content`类型。

### aside {#aside}

Aside 元素用来表示和当前文档内容相关的区块，比如广告、相关链接以及其他和当前文档相关的内容。

aside元素属于`Sectioning content`类型。

### h1,h2,...h6 {#h1h2h6}

这些元素用来标记对应区块的标题，其中h1为最高级别，h6为最低级别的子标题。 合理使用标题元素，也有利于搜索引擎对页面内容的理解。

建议使用标题元素来组织文档的大纲。在chrome浏览器中，安装"html5 outline"扩展可查看文档大纲。

一般而言，一个页面应该只有一个一级标题。

这些元素属于`Heading content`类型。

### header {#header}

header元素不同于head元素，header用来标记文档的简介或者导航区域。

### footer {#footer}

footer元素通常包括版权信息、相关文档、机构简介等等内容。

