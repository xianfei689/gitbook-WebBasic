# 1、js使用方式

就像在HTML中使用CSS一样，必须通过适当的方法将JavaScript和HTML结合起来使用，JavaScript只有被嵌入到HTML中时才能对网页产生作用。和使用CSS的方式类似，在HTML中使用JavaScript的方式有三种，即嵌入式、行内式和链接式。

## 嵌入式 <a id="&#x5D4C;&#x5165;&#x5F0F;"></a>

所谓嵌入式使用JavaScript的方法就是利用script元素将脚本嵌入到网页中。Script元素是HTML语言为了引入脚本程序而定义的一个标记，插入脚本的具体方法是：把脚本用script元素标记后，放在HTML文件中的head部分或者body部分。虽然script脚本既可以放在head部分和body部分，但比较好的做法是将所有包含预定义函数的脚本放在head部分，因为HTML的内容在浏览器中处理时是从上到下解释的，放在head中的脚本比放在body中的脚本先处理。这样，浏览器在处理body中的元素内容时需要用到的JavaScript功能已经预先装载，减少出错的可能。同样的道理，如果JavaScript脚本需要等到页面完全装载完毕才要使用，则将其放置在body部分末尾。

使用script元素标记标本的语法如下：

```markup
<script >
    脚本内容
</script>
```

下面的HTML代码创建了一行文本，当用户单击文本时，文字会改变为其它内容。

```markup
<!DOCTYPE html>
<html lang="zh">

<head>
    <meta charset="utf-8" />
    <title>嵌入式JavaScript案例</title>
    <script>
    function hello() {
        document.getElementById("demo").innerHTML = "你好，JavaScript世界！";
    }
    </script>
</head>

<body>
    <p id="demo" onclick="hello()">单击这段文字!</p>
</body>

</html>
```

在上述代码中，onclick="hello\(\)"表示当鼠标单击时执行hello\(\)函数功能，而display函数就是用script元素标记的嵌入式脚本。

## 行内式 <a id="&#x884C;&#x5185;&#x5F0F;"></a>

所谓行内式脚本应用就是将脚本内容写在HTML元素的标记中，在这些标记中，将事件和相应内容写在一起。 如上例的HTML代码，如果用行内式的写法可以修改如下，而执行结果是完全相同的：

```markup
<!DOCTYPE html>
<html lang="zh">

<head>
    <meta charset="utf-8" />
    <title>行内式JavaScript案例</title>
</head>

<body>
    <p id="demo" onclick="javascript:alert('Hello!');">单击这段文字!</p>
</body>

</html>
```

从上述代码可以看到，行内式的写法似乎更加简洁，但是，在实际工作中，我们要尽量避免这种写法，因为行内式嵌入的脚本可读性很差，不容易维护，不符合Web标准中将内容、表现、行为三者相分离的原则。而且，但从效率的角度来讲，如果某个功能要反复使用，则行内式的写法将会过于繁琐，反倒是其它写法更加简洁。故而，行内式使用脚本的方式仅限于较为简单的情况。

## 链接式 <a id="&#x94FE;&#x63A5;&#x5F0F;"></a>

所谓链接式就是将JavaScript脚本文件单独写在后缀名为js的文件中，然后在需要使用此脚本的网页中加入脚本文件的路径名称即可。这种方式使用的脚本可以链接到多个网页甚至多个网站中，提高了代码的重用性，也方面了维护，同时也能降低网站主机访问次数，提高网站性能。

要引用外部js文件，需要在合适的地方，一般为HTML文件的head部分，使用script元素来指定外部脚本存放的路径和名称。

还是以上述中的HTML为例，如果改写成链接式引用，则需要将脚本存放成单独的文件，HTML文档代码如下：

```markup
<!DOCTYPE html>
<html lang="zh">

<head>
    <meta charset="utf-8" />
    <title>链接式JavaScript案例</title>
    <script src="js/hello.js"></script>
</head>

<body>
    <p>链接式JavaScript案例</p>
</body>

</html>
```

其中使用src属性引用的hello.js文件存放在HTML文件的同一级目录中，外部hello.js文件内容如下：

```markup
alert('Hi');
```

