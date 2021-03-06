# 10、reset css

在现实中，用户使用的浏览器五花八门，比如IE、Firefox、Chrome、Safari等等，每个浏览器都有各自默认的显示HTML元素的样式，这些默认的样式可能并不相同。为了确保浏览器的兼容性，前端开发人员普遍采用重置样式表（CSS Reset）的办法。

重置样式表的思路非常简单：即为HTML元素预设一套样式，然后将其应用到所有浏览器。所谓重置样式，通常指的是移除元素的大小、外边距、内边距和其他样式。因为CSS可以级联，只要确保重置样式位于自定义样式之前，那么不同浏览器再渲染使用了重置样式表的页面时，会先重置样式表，然后再按照前端开发人员设置的样式来显示页面，这样达到了最大化统一不同浏览器显示效果的目的。例如：

```css
    <link rel="stylesheet" href="reset.css">
    <link rel="stylesheet" href="main.css">
```

在网络上，我们可以看到有大量存在细微差异的重置样式表的方法，其中最流行的是[Eric Meyer提供的CSS Reset文件](http://meyerweb.com/eric/tools/css/reset/)。除了强制重置样式之外，我们还可以选择不那么激进的Normalize.css方法，这种方法保留了大多数浏览器默认样式。

