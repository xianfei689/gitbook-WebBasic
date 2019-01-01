## CSS过渡及动画 {#css过渡及动画}

CSS3的一个革新之处，是可以实现过渡及动画，前端开发人员现在可以不借助于Flash或者JavaScript，仅通过HTML和CSS就实现动画效果。

借助于CSS3的过渡，我们可以在特定事件发生时，改变元素的外观。CSS3动画还可以设定多个关键帧。这样实现不同状态之间的变化。

### 过渡 {#过渡}

若要过渡生效，元素必须在状态上有所改变，并且为不同的状态分配两个不同的样式。最简单的改变状态的方式就是使用:hover、 :focus、 :active和 :target 伪类。 和过渡相关的属性有四个，分别是transition-property、transition-duration、transition-timing-function和 transition-delay。创建一个过渡，并不需要以上四个属性，前三个是使用得最多的。

下面是个过渡效果的例子：

```css
.box {
  background: #2db34a;
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
}
```

上述例子中，当鼠标移动到矩形之上时，矩形的背景色会在1秒之内发生变化。

#### 过渡属性 {#过渡属性}

transition-property 属性决定元素的哪些属性会发生过渡变化。默认情况下，不同状态之间的所有不同值得属性都会有过渡变化效果。但我们可以通过transition-property属性来具体指定需要有过渡效果的属性。比如，上述的例子中，我们指定了背景background作为唯一的过渡效果属性。

可以指定多个属性作为过渡效果，多个属性之间用逗号隔开。例如：

```css
.box {
    background: #2db34a;
    border-radius: 6px
    transition-property: background, border-radius;
    transition-duration: 1s;
    transition-timing-function: linear;
  }
  .box:hover {
    background: #ff7b29;
    border-radius: 50%;
  }
```

上例中，元素会同时在背景色和圆角效果上产生过渡。

非常重要的一点是，并非所有的属性都可以用在过渡效果上，只有那些拥有确定的中值得属性才可以用在过渡效果。例如颜色、字体大小等等，但如display属性，就不能用在过渡效果上。常用的可以用在过渡效果的属性有：

1. background-color
2. background-position
3. border-color
4. border-width
5. border-spacing
6. bottom
7. clip
8. color
9. crop
10. font-size
11. font-weight
12. height
13. left
14. letter-spacing
15. line-height
16. margin
17. max-height
18. max-width
19. min-height
20. min-width
21. opacity
22. outline-color
23. outline-offset
24. outline-width
25. padding
26. right
27. text-indent
28. text-shadow
29. top
30. vertical-align
31. visibility
32. width
33. word-spacing
34. z-index

### 过渡效果持续时间 {#过渡效果持续时间}

Transition-duration属性用来指定过渡效果的持续时间，其单位可以是秒s，也可是毫秒ms，既可以整数，也可以是小数。

当指定了多个过渡属性时，CSS3还可分别为多个过渡效果指定持续时间。例如：

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition-property: background, border-radius;
  transition-duration: .2s, 1s;
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;
}
```

上例中，背景色的过渡会在0.2秒之内完成，而圆角效果的过渡会在1秒之内完成。

### 过渡的缓动效果设置 {#过渡的缓动效果设置}

Transition-timing-function 属性用来设定过渡效果的变化速度。主要值有：linear、 ease-in、 ease-out 和 ease-in-out。

linear值表示变化的时候以恒定的速度进行过渡。ease-in表示过渡的时候，先慢后快，而ease-out表示先快后慢，ease-in-out表示开始慢，中间快，结束前有缓速的过渡。缓动效果还可参考网站[cubic-bezier Builder](http://www.roblaplaca.com/examples/bezierBuilder/)自行定义，

当有多个过渡属性时，我们可以分别其指定过渡速度设置，也是用逗号隔开。

### 过渡效果的延迟设置 {#过渡效果的延迟设置}

transition-delay属性用来指定过渡效果在多久之后发生，其单位也是时间单位。这一属性的用法和上述属性类似，不再赘述。

### 过渡效果的简写 {#过渡效果的简写}

过渡效果的设置，和背景、字体等属性一样，也可以简写，使用transition属性，依次设置transition-property、 transition-duration、 transition-timing-function以及transition-delay。不同的属性时间用空格隔开，多个过渡效果之间用逗号隔开。例如：

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition: background .2s linear, border-radius 1s ease-in 1s;
}
.box:hover {
  color: #ff7b29;
  border-radius: 50%;
}
```

上例中，背景色在0.2秒之内匀速过渡，而圆角效果在1秒之后，先慢后快地在1秒内完成过渡。

### 变形和过渡的结合 {#变形和过渡的结合}

下面，我们将变形和过渡结合起来，实现图片翻转的动画效果。其中，HTML部分：

```php
<div class="card-container">
    <div class="card">
        <div class="side">
            <img src="https://img1.doubanio.com/view/photo/photo/public/p2329615548.jpg" alt="海拉尔的冬">
        </div>
        <div class="side back">海拉尔的冬</div>
    </div>
</div>
```

CSS部分：

```css
.card-container {
    cursor: pointer;
    height: 150px;
    perspective: 200;
    position: relative;
    width: 150px;
}

.card {
    height: 100%;
    position: absolute;
    transform-style: preserve-3d;
    transition: all 1s ease-in-out;
    width: 100%;
}

.card:hover {
    transform: rotateY(180deg);
}

.side {
    backface-visibility: hidden;
    border-radius: 6px;
    height: 100%;
    position: absolute;
    overflow: hidden;
    width: 100%;
}

.back {
    background: #eaeaed;
    color: #0087cc;
    line-height: 150px;
    text-align: center;
    transform: rotateY(180deg);
}
```

其中用到了绝对定位，使得图片和文字处于相同容器的相同位置，而图片背部的描述文字，通过绕Y轴旋转180度后，再旋转过来之后，就实现文字的正常显示。

### 动画 {#动画}

过渡最适合构建那些状态有变化的动画，而要做更加复杂的动画，最好的选择是使用animation属性。

#### 关键帧 {#关键帧}

为了设定动画过程，需要使用@keyframes 指定关键帧，@keyframes 的规则包含动画名称、动画断点以及产生变化的属性。例如：

```
@keyframes slide {
  0% {
    left: 0;
    top: 0;
  }
  50% {
    left: 244px;
    top: 100px;
  }
  100% {
    left: 488px;
    top: 0;
  }
}
```

上例中，动画名称为slide，有三个关键帧断点，使用定位关键词产生位置上的变化。还可以使用关键词from to 表示0\%和100\%。

#### 动画名称 {#动画名称}

使用keyframes指定关键帧时，需要命名动画名称\(animation-name\)，该名称将在元素声明动画（animation）属性时使用。例如：

```
.stage:hover .ball
{
animation-name
:
 slide
;
}
```

#### 动画持续时间、缓动效果及延迟 {#动画持续时间、缓动效果及延迟}

和过渡属性类似，动画属性也有持续时间（animation-duration）、缓动效果（animation-timing-function）及延迟属性（animation-delay）。例如：

```
.stage:hover .ball
{
animation-name
:
 slide
;
animation-duration
:
 2s
;
animation-timing-function
:
 ease-in-out
;
animation-delay
:
 .5s
;
}
```

#### 动画重复次数 {#动画重复次数}

默认情况下，动画只执行一次，我们可以通过animation-iteration-count属性指定重复次数，其值可以是整数，还可以是infinite关键字，使用infinite关键字后，动画效果将无限循环。

#### 动画方向 {#动画方向}

动画运行的方向，可以通过nimation-direction属性来指定，其值有normal, reverse, alternate 和 alternate-reverse。

1. **normal**
   0-
   &gt;
   100；
2. **reverse**
   100-
   &gt;
   0；
3. **alternate**
   0-
   &gt;
   100-
   &gt;
   0；
4. **alternate-reverse**
   100-
   &gt;
   0-
   &gt;
   100；

其中，后两个值，需要和动画重复次数配合使用。

#### 动画运行状态 {#动画运行状态}

通过animation-play-state可以在动画运行过程中暂停，默认值为running，即不暂停，若其值为paused，则点击动画元素，可暂停其动画。

#### 动画填充模式 {#动画填充模式}

动画填充模式（animation-fill-mode）指定元素在动画执行之前、之后或者前后的状态，其值为none, forwards, backwards 和 both。

#### 动画属性简写 {#动画属性简写}

和过渡属性类似，动画属性也可以简写，顺序为animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction, animation-fill-mode, 最后为 animation-play-state。例如：

```
.stage:hover .ball
{
animation
:
 slide 2s linear
;
}
```

### 动画库animate.css的使用 {#动画库animatecss的使用}

在实际工作中，动画效果的调试是个非常繁琐的工作，因此，涌现出一批CSS的动画库，其中[animate.css](http://daneden.github.io/animate.css/)由于动画效果丰富，因此使用较多。

animate.css的用法非常简单，引入样式表后，在需要动画效果的元素起始标签中添加animated和相应动画效果的标签即可。例如：

```
<
div
>
<
h1 class=
"animated fadeInRight"
>
中国制造进入专利维权“反攻期”？
<
/h1
>
<
p class=
"animated bounceInLeft"
>
当中国企业屡屡在“海外专利战”中被“穷追猛打”时，华为却意外打出了“专利反围剿”的关键一枪。
<
/p
>
<
/div
>
```

其中fadeInRight、bounceInLeft为animate.css提供的动画效果。

