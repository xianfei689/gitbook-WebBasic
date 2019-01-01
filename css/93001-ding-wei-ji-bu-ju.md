## 定位及布局 {#定位及布局}

### 信息流 {#信息流}

浏览器在呈现信息时会按照元素的类型进行处理，它将块元素从上到下显示（块元素与块元素之间另起一行），将行内元素按语言方向水平显示（如汉字、英语是从左到右，维吾尔语、阿拉伯语等有些语言是从右到左），行内元素直到到达容器边缘时才换行显示，这种显示元素的方式叫做页面的正常流。

常见的大多数元素属于块元素，如p、table、div、li、ul、ol、object、h1-h6等等，行内元素有a、span、img、b、strong等等。需要注意的是，匿名内容（即没有使用元素标签标注的内容）也按行内元素处理。

### display {#display}

元素如何显示，可以通过display属性进行指定。每一个元素都有一个默认的display属性，但这个属性值可以修改。块元素和行内元素可通过display属性改变它们的显示方式，比如在某些情景，编辑人员需要给行内元素添加高度，以改进元素的显示效果，行内元素是无法直接通过width属性指定高度的，但可以通过display属性将其变为块元素，再为其添加高度。

display有很多属性值，最常用的是block、inline、inline-block以及none。其中block将元素按照块元素方式显示；inline将元素按照行内元素显示；而inline-block模式将使元素像行内元素那样显示，但同时又具有bolock元素的特征，可以赋予宽度和高度等等；none模式将元素整体隐藏起来，相当于该元素不存在一样，元素一旦声明其display的值为none，包含在内部的内容及其后代元素都会隐藏，并且其内容和后代不能再通过display改变显示方式。

### 浮动 {#浮动}

除了相对定位和绝对定位能控制元素在正常流的位置之外，CSS还提供了浮动（float）机制来控制元素在正常流中的位置，在实际工作中，float属性是主要的定位、排版手段。从页面栏目的划分到图片的定位，大都通过float属性实现。

浮动的值有left、right和none，其中左浮动将会使得块元素浮动向所在父元素的左侧，其后续的内容将出现在该元素的右侧，并和该元素的顶端对齐。右浮动刚好相反，none则没有浮动效果。

先看一段HTML代码：

```php
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<title>浮动</title>
<style>
#head {
    border:1px #CCC solid;
    width:410px;
    height:100px;
    margin-bottom:10px;
}
#main {
    border:1px #CCC solid;
    width:400px;
    height:200px;
    margin-bottom:10px;
    padding:5px;
}
#left {
    border:1px #CCC solid;
    width:198px;
    height:198px;
}
#right {
    border:1px #CCC solid;
    width:193px;
    height:198px;
    margin-left:5px;
}
</style>
</head>
<body>
<div id="head">头部</div>
<div id="main">
  <div id="left">左侧</div>
  <div id="right">右侧</div>
</div>
</body>
</html>
```

这段代码的显示效果如下：

![](https://yangjh.gitee.io/front-end/images/beforefloat.jpg "浮动前")

下面，我们为left和right添加浮动属性。float属性有三个值：none（不浮动）、left（左浮动）、right（右浮动），其中none是默认值。盒元素必须为其指定明确的宽度值，才能应用浮动属性。

```css
#left {
    border:1px #CCC solid;
    width:198px;
    height:98px;
    float:left;
}
#right {
    border:1px #CCC solid;
    width:193px;
    height:98px;
    margin-left:5px;
    float:left;
}
```

显示效果如下：

![](https://yangjh.gitee.io/front-end/images/float.jpg "浮动")

我们看到id为right的div元素现在和id为left的div元素在同一水平位置上显示，并非另起一行。浮动的方向是针对使用了浮动元素的位置而言的，并不应用于其后的元素。另外一定要注意，如果一个元素没有宽度大小，则不能指定浮动效果。

常见的图文混排效果，就是通过浮动来实现。

```php
<div class="item">
<div class="img_area">
<a target="_blank" href="http://zhibo.qq.com/mbask/1844/index.html">
<img src="http://t3.qlogo.cn/mbloghead/72f0353448bac74e1d86/50" 
alt="罗崇敏：安全不保 何谈教育" title="罗崇敏：安全不保 何谈教育">
</a>
</div>
<div class="text_area">
<h5>
罗崇敏，中共云南省委高校工委书记，云南省教育厅长
<a class="more" target="_blank" href="http://zhibo.qq.com/mbask/1844/index.html">[详细]</a>
</div>
</div>
<div class="item">
<div class="img_area">
<a target="_blank" href="http://zhibo.qq.com/mbask/1833/index.html">
<img src="http://t3.qlogo.cn/mbloghead/ca99366b03bb20d692bc/50" 
alt="王旭明：如何避免校车惨剧一再发生" title="王旭明：如何避免校车惨剧一再发生">
</a>
</div>
<div class="text_area">
<h5>
<a target="_blank" href="http://zhibo.qq.com/mbask/1833/index.html">王旭明：如何避免惨剧再发生</a>
</h5>
王旭明，教育部语文出版社社长，原教育部新闻发言人
<a class="more" target="_blank" href="http://zhibo.qq.com/mbask/1833/index.html">[详细]</a>
</div>
</div>
```

在这个例子中，图片和文字分别作为内容放在div元素中，这两个div容器为“img\_area”和“text\_area”， “img\_area”和“text\_area”是div容器的类名称（使用了class属性），这两个div元素又是类名为item的容器的内容，类名为item的div元素可以重复使用，如上例中，就有两个类名为item的div元素。如果不使用浮动，文字没有办法完美环绕在图片周围，将图片放入类名为img\_area的div元素中，并把文字放在类名为text\_area的div元素中，使用如下样式，即可达到效果：

```css
.img_area {
    float: left;
    padding: 3px 10px 0 0;
    width: auto;
}
.text_area {
    line-height: 20px;
}
.item {
    padding: 0 5px 5px;
    text-align: left;
}
```

其中花括弧外面的“.img\_area”为选择符，.img\_area表示该选择符为类选择符，对应HTML中class为img\_area的元素，“float：left”表示选择符对应的元素将左浮动，“padding: 3px 10px 0 0;”语句声明选择符对应元素上右下左的内边距分别为3像素、10像素、0和0，最后width表示该元素的宽度将根据所包含内容的大小计算而来。另外两个CSS规则用来设定文字区域的行间距和整体的内边距、对齐方式。

在这个例子中，我们看到了浮动的特点，首先，类名为img\_area的div元素声明了左浮动的规则，这样，这个div元素就改变了它默认的块元素显示方式，而是尽可能得向父元素（类名为item的div元素）的左上角靠齐，并且，它右侧的空间将会被后续的元素所填充，因此，尽管类名为text\_area的div元素没有声明浮动，但它还是占据了类名为img\_area元素的右侧空间。这样，我们就达到了图文混编的效果。

### 清除浮动 {#清除浮动}

从上面的例子中，我们清楚地看到，使用了浮动属性的元素将会影响到其后的内容。这种影响有时候是我们期望的，有时候是我们所不乐见的。如下图所示：

![](https://yangjh.gitee.io/front-end/images/beforeclear.jpg "清除浮动前")

图中的HTML及CSS如下：

```php
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>浮动清除实例</title>
<style type="text/css">
body {
    font-size:14px;
    text-align:center;
}
.item {
    height:115px;
    width:500px;
    border:1px #ccc solid;
    padding:10px;
    margin:20px;
}
.float_area {
    border:1px #ccc solid;
    width:100px;
    float:left;
    margin:0 10px 10px 0;
}
.normal_area {
    border:1px #ccc solid;
    width:210px;
}
.float_area,.normal_area {
    height:50px;
    line-height:50px;
}
</style>
</head>
<body>
<div class="item">
  <div class="float_area">左浮动模块</div>
  <div class="float_area">左浮动模块</div>
  <div class="normal_area">希望按正常流显示的模块</div>
</div>
</body>
</html>
```

在上面的代码中，类名为float\_area的div元素使用了左浮动，但是我们不希望类名为normal\_area的div元素正常显示，也就是另起一行显示时，我们就必须使用clear属性来清除浮动，如下图所示。

clear的值有left、right、both和none，其中left表示清除左浮动，right表示清除右浮动，both表示清除左、右两侧的浮动影响，而none表示不清除浮动。

![](https://yangjh.gitee.io/front-end/images/clear.jpg "清除浮动")

上图中的HTML和CSS如下：

```php
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>浮动清除实例</title>
<style type="text/css">
body {
    font-size:14px;
    text-align:center;
}
.item {
    height:115px;
    width:500px;
    border:1px #ccc solid;
    padding:10px;
    margin:20px;
}
.float_area {
    border:1px #ccc solid;
    width:100px;
    float:left;
    margin:0 10px 10px 0;
}
.normal_area {
    border:1px #ccc solid;
    width:210px;
    clear:both;
}
.float_area,.normal_area {
    height:50px;
    line-height:50px;
}
</style>
</head>
<body>
<div class="item">
  <div class="float_area">左浮动模块</div>
  <div class="float_area">左浮动模块</div>
  <div class="normal_area">希望按正常流显示的模块</div>
</div>
</body>
</html>
```

在本例中，我们需要类名为normal\_area的div元素不和左浮动模块并排显示，而是另起一行，因此，我们为其声明了“clear：both”的CSS规则，该规则表示将类名为normal\_area的div元素不受之前左右浮动元素的影响，具体到上例中，“clear：both”完全可以用“clear：left”代替，显示效果是一致的。 除了上述的方法外，我们还可以在需要清除浮动的地方插入空白div，为其声明内嵌样式表，在样式表中声明clear属性即可。如下例所示：

```php
<div class="item">
  <div class="float_area">左浮动模块</div>
  <div class="float_area">左浮动模块</div>
  <div style=”clear:both;”></div>
  <div class="normal_area">希望按正常流显示的模块</div>
</div>
```

这种方法对于初学者容易理解和掌握，但内容为空的div元素，在语义上并不十分完美，实际工作中广泛采用的是名为“clearfix”的一种技巧：

```php
.clearfix:before,.clearfix:after {
    display: table;
  content: " ";
}
.clearfix:after {
    clear:both;
}
```

这种clearfix方案，生成了两个伪元素，并将其display设置成table。这将创建一个匿名的table-cell和一个新的块状区域，这意味着：:before伪元素阻止了顶部边缘塌陷。而:after伪元素清除了浮动。其结果是，只需要在包含浮动元素的容器上添加class=“clearfix”属性，没有必要专门添加HTML元素，减少清楚浮动所需的代码量，提高了工作效率。

在CSS中，和定位相关的常用属性有position、top、right、bottom、left、z-index。通过这些属性，设计人员可以控制元素的精确定位。

### position {#position}

position属性用来设定对象的定位方式。它的值有：

1. **static**
   对象遵循常规流。top，right，bottom，left等属性不会被应用,static是position属性的默认值。
2. **relative**
   对象遵循常规流，并且参照自身在常规流中的位置通过top，right，bottom，left属性进行偏移时不影响常规流中的任何元素。
3. **absolute**
   对象脱离常规流，使用top，right，bottom，left等属性进行绝对定位，盒子的偏移位置不影响常规流中的任何元素，其margin不与其他任何margin折叠。
4. **fixed**
   对象脱离常规流，使用top，right，bottom，left等属性以窗口为参考点进行定位，当出现滚动条时，对象不会随着滚动。
5. **center**
   对象脱离常规流，使用top，right，bottom，left等属性指定盒子的位置或尺寸大小。盒子在其包含容器垂直水平居中。盒子的偏移位置不影响常规流中的任何元素，其margin不与其他任何margin折叠。（CSS3新增属性）
6. **page**
   盒子的位置计算参照absolute。盒子在分页媒体或者区域块内，盒子的包含块始终是初始包含块，否则取决于每个absolute模式。（CSS3新增属性）
7. **sticky**
   对象在常态时遵循常规流。它就像是 relative 和 fixed 的合体，当在屏幕中时按常规流排版，当卷动到屏幕外时则表现如fixed。该属性的表现是现实中你见到的吸附效果。（CSS3新增属性）

其中relative和absolute方式使用较多，它们的区别可从下面的例子中看出：

  


