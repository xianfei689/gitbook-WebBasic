# 9、定位及布局

## 信息流 <a id="&#x4FE1;&#x606F;&#x6D41;"></a>

浏览器在呈现信息时会按照元素的类型进行处理，它将块元素从上到下显示（块元素与块元素之间另起一行），将行内元素按语言方向水平显示（如汉字、英语是从左到右，维吾尔语、阿拉伯语等有些语言是从右到左），行内元素直到到达容器边缘时才换行显示，这种显示元素的方式叫做页面的正常流。

常见的大多数元素属于块元素，如p、table、div、li、ul、ol、object、h1-h6等等，行内元素有a、span、img、b、strong等等。需要注意的是，匿名内容（即没有使用元素标签标注的内容）也按行内元素处理。

## display <a id="display"></a>

元素如何显示，可以通过display属性进行指定。每一个元素都有一个默认的display属性，但这个属性值可以修改。块元素和行内元素可通过display属性改变它们的显示方式，比如在某些情景，编辑人员需要给行内元素添加高度，以改进元素的显示效果，行内元素是无法直接通过width属性指定高度的，但可以通过display属性将其变为块元素，再为其添加高度。

display有很多属性值，最常用的是block、inline、inline-block以及none。其中block将元素按照块元素方式显示；inline将元素按照行内元素显示；而inline-block模式将使元素像行内元素那样显示，但同时又具有bolock元素的特征，可以赋予宽度和高度等等；none模式将元素整体隐藏起来，相当于该元素不存在一样，元素一旦声明其display的值为none，包含在内部的内容及其后代元素都会隐藏，并且其内容和后代不能再通过display改变显示方式。

## 浮动 <a id="&#x6D6E;&#x52A8;"></a>

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

![&#x6D6E;&#x52A8;&#x524D;](https://yangjh.gitee.io/front-end/images/beforefloat.jpg)

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

![&#x6D6E;&#x52A8;](https://yangjh.gitee.io/front-end/images/float.jpg)

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

## 清除浮动 <a id="&#x6E05;&#x9664;&#x6D6E;&#x52A8;"></a>

从上面的例子中，我们清楚地看到，使用了浮动属性的元素将会影响到其后的内容。这种影响有时候是我们期望的，有时候是我们所不乐见的。如下图所示：

![&#x6E05;&#x9664;&#x6D6E;&#x52A8;&#x524D;](https://yangjh.gitee.io/front-end/images/beforeclear.jpg)

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

![&#x6E05;&#x9664;&#x6D6E;&#x52A8;](https://yangjh.gitee.io/front-end/images/clear.jpg)

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

## position <a id="position"></a>

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

```php
<!DOCTYPE HTML>
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>相对定位与绝对定位</title>
    <style type="text/css">
      body {
        width:960px;
        margin: 0 auto;
        font-family: 微软雅黑;
        font-size: 18px;
        line-height: 1.8em;
      }
      div {
        width: 300px;
        float: left;
      }
      .relative {
        position: relative;
        top:150px;
      }
      .absolute {
        position: absolute;
        top:150px;
      }
      .bg {
        background-color: #fcc;
      }
    </style>
  </head>
  <body>
    <div>
      <h2>正常信息流</h2>
      <p>孩子，你真是快活啊，一早晨坐在泥土里，耍着折下来的小树枝。</p>
      <p>我微笑着看你在那里耍着那根折下来的小树枝。</p>
      <p class="bg">我正忙着算账，一小时一小时在那里加叠数字。</p>
      <p>也许你在看我，想到：“这种好没趣的游戏，竟把你的一早晨的好时间浪费掉了!"</p>
      <p>孩子，我忘了聚精会神玩耍树枝与泥饼的方法了。</p>
    </div>
    <div>
      <h2>相对定位</h2>
      <p>孩子，你真是快活啊，一早晨坐在泥土里，耍着折下来的小树枝。</p>
      <p>我微笑着看你在那里耍着那根折下来的小树枝。</p>
      <p class="bg relative">我正忙着算账，一小时一小时在那里加叠数字。</p>
      <p>也许你在看我，想到：“这种好没趣的游戏，竟把你的一早晨的好时间浪费掉了!"</p>
      <p>孩子，我忘了聚精会神玩耍树枝与泥饼的方法了。</p>
      <code>.relative { position: relative; top:150px;}</code>
    </div>
    <div>
      <h2>绝对定位</h2>
      <p>孩子，你真是快活啊，一早晨坐在泥土里，耍着折下来的小树枝。</p>
      <p>我微笑着看你在那里耍着那根折下来的小树枝。</p>
      <p class="bg absolute">我正忙着算账，一小时一小时在那里加叠数字。</p>
      <p>也许你在看我，想到：“这种好没趣的游戏，竟把你的一早晨的好时间浪费掉了!"</p>
      <p>孩子，我忘了聚精会神玩耍树枝与泥饼的方法了。</p>
      <code>.absolute {
        position: absolute;
        top:150px;}
      </code>
    </div>
  </body>
</html>
```

上例的运行结果如下图所示：

![&#x4E0D;&#x540C;&#x5B9A;&#x4F4D;&#x65B9;&#x5F0F;&#x7684;&#x533A;&#x522B;](https://yangjh.gitee.io/front-end/images/position.png)

需要说明的是，absolute方式定位的坐标原点默认为body元素的坐标原点，在上例中，使用绝对定位的元素虽然包含在第三个div元素中，但计算它的位置时，还是从body元素的顶部开始。

如果想要使absolute相对于所在父元素定位，则需要使父元素的position取值relative。如下例：

```php
<!DOCTYPE HTML>
<html>

<head>
    <meta charset="utf-8">
    <title>绝对定位的参照系</title>
    <style type="text/css">
    body {
        width: 960px;
        margin: 0 auto;
        font-family: 微软雅黑;
        font-size: 18px;
        line-height: 1.8em;
    }

    div {
        width: 400px;
        float: left;
        margin: 0 20px 0 0
    }

    .absolute {
        position: absolute;
        left: 50px;
    }

    .bg {
        background-color: #fcc;
    }

    code {
        background-color: #ccc;
        height: 50px;
        line-height: 50px;
        display: block;
    }
    </style>
</head>

<body>
    <div>
        <h2>以body为参照</h2>
        <p>孩子，你真是快活啊，一早晨坐在泥土里，耍着折下来的小树枝。</p>
        <p>我微笑着看你在那里耍着那根折下来的小树枝。</p>
        <p class="bg absolute">我正忙着算账，一小时一小时在那里加叠数字。</p>
        <p>也许你在看我，想到：“这种好没趣的游戏，竟把你的一早晨的好时间浪费掉了!"</p>
        <p>孩子，我忘了聚精会神玩耍树枝与泥饼的方法了。</p>
        <code>.absolute { position: absolute; left:50px;}
      </code>
    </div>
    <div>
        <div style="position:relative">
            <h2>以父元素为参照</h2>
            <p>孩子，你真是快活啊，一早晨坐在泥土里，耍着折下来的小树枝。</p>
            <p>我微笑着看你在那里耍着那根折下来的小树枝。</p>
            <p class="bg absolute">我正忙着算账，一小时一小时在那里加叠数字。</p>
            <p>也许你在看我，想到：“这种好没趣的游戏，竟把你的一早晨的好时间浪费掉了!"</p>
            <p>孩子，我忘了聚精会神玩耍树枝与泥饼的方法了。</p>
            <code>.absolute { position: absolute; left:50px;}
        </code>
        </div>
    </div>
</body>

</html>
```

上例的运行结果见：

![&#x7EDD;&#x5BF9;&#x5B9A;&#x4F4D;&#x7684;&#x53C2;&#x7167;&#x539F;&#x70B9;](https://yangjh.gitee.io/front-end/images/absolute.png)

## top、right、bottom、left <a id="top&#x3001;right&#x3001;bottom&#x3001;left"></a>

top、right、bottom、left属性用来设置对象参照相对物顶边界向下、向左、向上、向右偏移的位置，这四个属性的值可以是正值，也可以是负值，可以是整数，也可以是百分比。必须定义position属性值为 relative 、absolute 、 fixed 、 center 、 page，此属性方可生效。

```css
top:50%;
right:10px;
bottom:100px;
left:0;
```

## clip <a id="clip"></a>

## z-index <a id="z-index"></a>

z-index属性用来设置对象的层叠顺序。同一个层叠上下文中，层叠级别（即z-index属性值）大的显示在上面，反之显示在下面。该属性对定义了position为 relative 、 absolute 、 fixed 、 center 、 page 、 sticky 的元素有效，如果只设定z-index属性，但不使用position属性，则z-index属性无效。例如：

```php
<!DOCTYPE HTML>
<html lang="zh">

<head>
    <meta charset="utf-8">
    <title>z-index属性演示</title>
    <style type="text/css">
    body {
        width: 960px;
        margin: 0 auto;
        font-family: 微软雅黑;
        font-size: 18px;
        line-height: 1.8em;
    }

    h1 {
        color: green;
    }

    div {
        width: 100px;
        height: 100px;
        text-align: center;
    }

    .index1 {
        position: absolute;
        left: 150px;
        top: 150px;
        background-color: #aaa;
    }

    .index2 {
        background-color: #ccc;
        position: absolute;
        left: 190px;
        top: 190px;
    }

    .index3 {
        position: absolute;
        left: 230px;
        top: 230px;
        z-index: 3;
        background-color: #eee;
    }

    .index4 {
        z-index: 4;
        background-color: #999;
    }
    </style>
</head>

<body>
    <h1>z-index属性只对使用了position属性的元素有效</h1>
    <div class="index4">z-index: 4</div>
    <div class="index1">z-index: 1</div>
    <div class="index2">z-index: 2</div>
    <div class="index3">z-index: 3</div>
</body>

</html>
```

上例中虽然为div.index4设定了z-index的值，但从运行效果（如下图所示）来看，这个z-index值显然没有起作用。

![z-index&#x5C5E;&#x6027;&#x6F14;&#x793A;](https://yangjh.gitee.io/front-end/images/z-index.png)

## CSS中的居中 <a id="css&#x4E2D;&#x7684;&#x5C45;&#x4E2D;"></a>

前面已经介绍，文字水平居中的方法为：

```css
text-align:center;
```

而元素的水平居中，通过设定margin-left和margin-right的值为auto实现，如：

```css
margin:0 auto;
```

单行文字的垂直居中，通过设定文字的行间距等于容器高度可以实现，例如：

```css
.center-text-trick {
  height: 100px;
  line-height: 100px;
}
```

多行文字的的垂直居中，可通过利用表格的垂直居中属性vertical-align来实现，例如：

```css
<div class="center-table">
  <p>I'm vertically centered multiple lines of text in a CSS-created table layout.</p>
</div>
.center-table {
  display: table;
  height: 250px;
  background: white;
  width: 240px;
  margin: 20px;
}
.center-table p {
  display: table-cell;
  margin: 0;
  background: black;
  color: white;
  padding: 20px;
  border: 10px solid white;
  vertical-align: middle;
}
```

元素的垂直居中，在不知道元素高度的情况下，可以通过绝对定位来实现，\[Citation not found\]例如：

```php
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>元素垂直居中实例</title>
    <style>
    main {
        background: white;
        height: 300px;
        margin: 20px;
        width: 300px;
        position: relative;
        resize: vertical;
        overflow: auto;
    }

    main div {
        position: absolute;
        top: 50%;
        left: 20px;
        right: 20px;
        background: black;
        color: white;
        padding: 20px;
        transform: translateY(-50%);
        resize: vertical;
        overflow: auto;
    }
    </style>
</head>

<body>
    <main>
        <div>
            我是一个块级元素，高度未知，我在父元素中垂直居中。
        </div>
    </main>
</body>

</html>
```

当我们不知道元素的宽度和高度时，可以使用如下的方法：

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

