# 11、CSS变形

使用transform属性，我们可以改变元素的大小、位置以及形状。transform属性有两套设置：二维和三维，这两套属性拥有不同的设置。

虽然浏览器对变形的支持还不是特别完美，但随着时间的推进，情况正在改善。最新版本的浏览器几乎都能支持CSS变形属性。

## CSS变形的语法 <a id="css&#x53D8;&#x5F62;&#x7684;&#x8BED;&#x6CD5;"></a>

变形属性的语法特别简单，就是在transform属性后设置变形的值。例如：

```css
div {
      transform: scale(1.5);
}
```

上例中的div元素，将在原有基础上放大1.5倍。

## 2D变形 <a id="2d&#x53D8;&#x5F62;"></a>

在CSS3中，元素可以在二维和三维空间中进行变形。二维变形在x轴和y轴，也就是水平和垂直方向进行；三维变形不但在x轴和y轴，还在Z轴上进行变形，三维变形不但可以改变元素长度和宽度，还可以调整元素的深度。下面我们先讨论2D变形。

### 2D旋转 <a id="2d&#x65CB;&#x8F6C;"></a>

Transform属性可以是旋转（rotate），通过设定rotate的值，可以旋转元素，正值为顺时针，负值则为逆时针，旋转时的默认原点为元素的中点，即水平和垂直方向的中点。如：

```css
.box-1 {
        transform: rotate(20deg);
    }

.box-2 {
        transform: rotate(-55deg);
    }
```

## 2D缩放 <a id="2d&#x7F29;&#x653E;"></a>

使用scale值，可以改变元素的比例。默认缩放比例为1，因此，小于1的值会缩小，大于1的值会放大。scale函数的值只有一个时，同时改变宽度和高度的比例，有两个值时，则分别表示宽度和高度的比例。还可以使用scaleX只改变元素的宽度，使用scaleY只改变元素的高度。例如：

```css
.box-3 {
        transform: scale(0.5);
    }

.box-4 {
        transform: scale(0.5, 1.5);
    }
```

## 2D位移 <a id="2d&#x4F4D;&#x79FB;"></a>

Translate有点像相对定位，能够将元素在不脱离正常文档信息流的情况下，移动其位置。使用translateX可以只改变水平位置，使用translateY可以只改变垂直位置。当然，也可以分别指定，两个值用逗号隔开。

```css
.box-5 {
    transform: translate(20px, 20%);
}

.box-6 {
    transform: translate(-50%);
}
```

位移的值可以是任何长度，单位常为像素或者百分比。translate的值如果为正值，则向右移动，否则相反。

## 2D倾斜 <a id="2d&#x503E;&#x659C;"></a>

倾斜（skew）可以实现元素在水平或者垂直方向的变形，它的用法和scale和translate相似。倾斜的值单位为角度。例如：

```css
.box-7 {
    transform: skew(15deg);
}

.box-8 {
    transform: skewY(15deg);
}

.box-9 {
    transform: skew(15deg, 15deg);
}
```

## 变形组合 <a id="&#x53D8;&#x5F62;&#x7EC4;&#x5408;"></a>

CSS的变形值，还可以组合使用，比如既有旋转，还有缩放等等。多个变形值之间用空格隔开即可。例如：

```css
transform: rotate(25deg) scale(.75);
```

## 设置变形的原点 <a id="&#x8BBE;&#x7F6E;&#x53D8;&#x5F62;&#x7684;&#x539F;&#x70B9;"></a>

前面已经提到，默认变形的原点是元素的中点。可以通过transform-origin属性设置变形的原点位置。

transform-origin属性可以接受1个或2个值。只有1个时，这个值同时为水平和垂直方向使用。如果为两个值，则第一个为水平方向，第二个为垂直方向。

transform-origin的值和背景图片的设置类似。

## 透视 <a id="&#x900F;&#x89C6;"></a>

为了使三维变形正常工作，就需要指定透视，所谓透视，指的是每个元素在视觉上的消失点，在三维空间的视角距离。

Perspective属性指定了观察者与z=0平面的距离，使具有三维位置变换的元素产生透视效果。z&gt;0的三维元素比正常大，而z&lt;0时则比正常小，大小程度由该属性的值决定。当值为0或负值时，无透视变换。例如：

```css
.box-10 {
    transform: perspective(100px) rotateX(15deg);
}

.box-11 {
    transform: perspective(1100px) rotateX(15deg);
}
```

## 3D旋转 <a id="3d&#x65CB;&#x8F6C;"></a>

三维变形不仅可以进行水平和垂直方向的变换，还可以改变物体的深度。之前，我们能在二维平面中顺时针或者逆时针旋转元素，现在，我们还可以在三个维度进行旋转。

使用rotateX值，可以使元素围绕X轴进行旋转；使用rotateY值，可以使得元素围绕y轴进行旋转；使用rotateZ值，可使元素围绕Z轴进行旋转。

同样的，围绕某个轴进行旋转时，正值表示顺时针，而负值表示逆时针。

## 3D缩放 <a id="3d&#x7F29;&#x653E;"></a>

使用scaleZ，可使元素在Z轴方向进行缩放。

## 3D位移 <a id="3d&#x4F4D;&#x79FB;"></a>

使用translateZ值，可使元素在Z轴方向位移。

## 变形风格 <a id="&#x53D8;&#x5F62;&#x98CE;&#x683C;"></a>

transform-style属性决定变形是在二维还是三维空间中进行，有两个值：flat和preserve-3d，默认为flat。

## 背部可见性 <a id="&#x80CC;&#x90E8;&#x53EF;&#x89C1;&#x6027;"></a>

进行三维变形后，元素背部的内容，有时需要设定可见性，默认情况下，元素背部的值是可见的。，如果要隐藏，则需要：

```css
backface-visibility: hidden;
```

