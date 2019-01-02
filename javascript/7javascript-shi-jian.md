# 7、JavaScript 事件

### 事件 <a id="&#x4E8B;&#x4EF6;"></a>

事件是JavaScript和DOM之间进行交互的桥梁，当某个事件发生时，通过它的处理函数执行相应的JavaScript代码。对于用户而言，常用的事件有鼠标事件、HTML事件和键盘事件。常见事件见表：

| 事件名 | 描述 |
| :--- | :--- |
| onclick | 点击鼠标左键时触发 |
| onmouseover | 鼠标指针移动到元素上时触发 |
| onmouseout | 鼠标指针移出元素时触发 |
| onload | 页面完全加载后触发 |
| onblue | 元素或者窗口失去焦点时触发 |
| onfocus | 元素或者窗口获得焦点时触发 |
| onsubmit | 提交表单时触发 |
| keydown | 按下键盘某个按键时触发 |
| keyup | 释放按键时触发 |

#### 事件监听方法 <a id="&#x4E8B;&#x4EF6;&#x76D1;&#x542C;&#x65B9;&#x6CD5;"></a>

**通用事件监听方法**

页面中的事件需要一个函数来响应，这类函数被成为事件监听函数（event listener），这些函数也被称为事件处理函数（event handler）。

可以直接在HTML标签中分配事件处理函数。几乎所有的HTML标签都支持onclick方法，例如：

```text
<p onclick="alert('我被点击了。');">Click me.</p>
```

这种方法在主流的浏览器中兼容性很强，但并不符合Web标准的原则——内容、表现和行为相互分离。因此，通常采用如下例所示的方法，即在脚本中设置事件监听函数。

```javascript
<!DOCTYPE html>
<html lang="zh">

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>事件监听函数</title>
    <style type="text/css" media="screen">
    body {
        width: 960px;
        margin: 0 auto;
        font: 18px/1.8em '微软雅黑';
    }

    p {
        font-size: 20;
        padding: 5px 0;
        font-weight: bolder;
    }
    </style>
    <script>
    window.onload = function() {
        //获取具体的对象
        var oP = document.getElementById('myP');
        // 设置事件监听函数
        oP.onclick = function() {
            alert('我被点击了。');
        }
    }
    </script>
</head>

<body>
    <div>
        <p id="myP">请点击我。</p>
    </div>
</body>

</html>
```

对于同一个事件，这两种方法都只能添加一个函数。而DOM则规定了另外一种方法，可以添加多个事件监听函数。

**DOM监听事件的方法**

DOM定义了两个方法分别用以添加和删除监听函数，即addEventListener\(\)和removeEventListener\(\)。这两个函数的语法如下：

```text
[object].addEventListener("事件名称",监听函数名称,是否用于捕获阶段);
[object].removeEventListener("事件名称",监听函数名称,是否用于捕获阶段);
```

利用这两个函数，可以为DOM中的节点添加或者删除多个事件监听函数，如：

```javascript
<!DOCTYPE html>
<html lang="zh">

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>DOM事件监听函数</title>
    <style type="text/css" media="screen">
    body {
        width: 960px;
        margin: 0 auto;
        font: 18px/1.8em '微软雅黑';
    }

    p {
        font-size: 20;
        padding: 5px 0;
        font-weight: bolder;
    }
    </style>
    <script>
    // 定义全局变量
    var oP;
    window.onload = function() {
        //获取具体的对象
        oP = document.getElementById('myP');
        // 添加监听函数
        oP.addEventListener("click",fnClick1,false);
        // 可以为某个事件添加多个监听函数
        oP.addEventListener("click",fnClick2,false);
    }
    function fnClick1 () {
        alert('这是fnClick1函数');
        // oP.removeEventListener("click",fnClick2,false);
    }
    function fnClick2 () {
        alert('这是fnClick2函数');
    }
    </script>
</head>

<body>
    <div>
        <p id="myP">请点击我。</p>
    </div>
</body>

</html>
```

这两个函数中的事件名称是类似与"click"、"load"的事件名称，而不是"onclick"、"onload"的事件名称。第三个参数如果是冒泡阶段，则为false，否则就是用于捕获阶段。[53](https://yangjh.gitee.io/front-end/js/jsevent.html#fn_53)

#### 事件对象 <a id="&#x4E8B;&#x4EF6;&#x5BF9;&#x8C61;"></a>

事件对象只在发生事件时才被创建，且只有事件处理函数才能访问。所有事件处理函数执行完毕后，事件对象就被销毁。事件对象，包含的信息如下：引起事件的对象；事件发生时鼠标的信息；事件发生时键盘的信息等等。

让开发人员郁闷的是，不同的浏览器，其事件对象的属性和方法不尽相同，有着较大的差异。

如何在这种添加事件方式下获取到事件对象？IE中event是作为全局对象的，所以直接使用event即可，如下：

```javascript
window.event
```

而W3C定义的DOM中，是把事件对象作为事件处理函数的第一个参数传入进去，如下：

```javascript
document.onclick = function (evt) {//事件对象只能在对应的事件处理函数内部可以访问到
alert(evt);
};
```

下面的案例，在不同的浏览器中，有着不同的输出：

```markup
<!DOCTYPE HTML>
<html lang="zh">

<head>
    <meta charset="utf-8">
    <title>event对象</title>
    <style type="text/css" media="screen">
    body {
        width: 960px;
        margin: 0 auto;
        font: 18px/1.8em '微软雅黑';
    }

    h1 {
        color: green;
    }

    p {
        font-size: 20;
        padding: 5px 0;
        font-weight: bolder;
    }
    </style>
</head>

<body>
    <h1>event对象</h1>
    <p>事件对象在不同的浏览器中访问的方法、其内置的属性和方法都不尽相同。比如以下代码在IE中无效：
    </p>
    <pre>
    document.onclick = function(evt) {
        for (var i = 0 in evt) {
            console.log(i + "=" + evt[i]);
        }
    };
    </pre>
    <script>
    document.onclick = function(evt) { //事件对象只能在对应的事件处理函数内部可以访问到
        for (var i = 0 in evt) {
            console.log(i + "=" + evt[i]);
        }
    };
    </script>
    <p>IE将event当作全局变量，当不过只有当事件发生时，event对象才有内容。</p>
    <pre>
    console.log(window.event); //null
    window.onload = function() {
        console.log(window.event);
    };</pre>
    <script>
    console.log(window.event); //null
    window.onload = function() {
        console.log(window.event);
    };
    </script>
</body>

</html>
```

> 53. 浏览器中的事件模型有两种，捕获型事件和冒泡型事件。冒泡型事件指的是事件从最特定的事件目标到最不特定的事件目标逐一触发。简单地说就是从DOM模型的底层向顶层逐层触发。而捕获型事件刚好相反，即从不确定的目标到最精确的目标逐一触发。IE浏览器不支持捕获型事件。[ ↩](https://yangjh.gitee.io/front-end/js/jsevent.html#reffn_53)

