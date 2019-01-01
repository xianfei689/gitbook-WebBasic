# 表单元素 {#表单元素}

## form {#form}

Form元素用来标记一组和表单相关的元素，如文本框、提交按钮等等内容，是服务器和用户进行交互的最重要元素。

form 元素最重要的两个属性是action和method，分别对应表单提交后的处理程序和表单提交方式。

```php
<form action="http://www.bing.com/search" method="get">
 <label>Bing: <input type="search" name="q"></label> <input type="submit" value="Search...">
</form>
```

## lable {#lable}

Label 元素用来标记表单交互元素的标签，是一个辅助说明性的元素，label元素往往对应特定的元素。

```php
<p><label>年龄: <input name=age type=number min=0></label></p>
```

## input {#input}

Input 元素通过type属性，可生成各种交互元素，如文本框、密码框、按钮等等。

| type | 类型 | 返回值 |
| :--- | :--- | :--- |
| hidden | 隐藏文本域 | 字符串 |
| text | 文本框 | 单行文本 |
| search | 搜索框 | 单行文本 |
| tel | 电话号码文本框 | 单行文本 |
| url | URL地址框 | URL地址 |
| email | 邮件地址框 | 邮箱地址或多个邮箱地址 |
| password | 密码框 | 单行文本 |
| date | 日期 | 无时区的日期 |
| time | 时间 | 无时区的时间 |
| number | 数字 | 数字 |
| range | 数字范围 | 数字 |
| color | 颜色选择器 | RGB颜色值 |
| checkbox | 复选框 | 列表值 |
| radio | 单选按钮 | 数字值 |
| file | 文件选择器 | 文件信息 |
| submit | 提交按钮 | 预设值 |
| image | 图片按钮 | 预设值 |
| reset | 重设按钮 | n/a |
| button | 按钮 | n/a |

Input 元素的用法示例如下：

```php
<input type="range" name="a" list="a-values">
<datalist id="a-values">
 <option value="10" label="Low">
 <option value="90" label="High">
</datalist>
```

## button {#button}

Button 元素生成一个按钮，可通过type属性控制按钮类型。type的值有reset、submit和button，分别对应重置按钮、提交按钮和普通按钮。

## select {#select}

Select 元素生成一个下拉菜单控制器，菜单列表由option构成。

```php
<select name="unittype" required>
 <option value=""> Select unit type </option>
 <option value="1"> Miner </option>
 <option value="2"> Puffer </option>
 <option value="3"> Snipey </option>
 <option value="4"> Max </option>
 <option value="5"> Firebot </option>
 </select>
```

## datalist {#datalist}

Datalist 可为指定的表单元素，如文本框，生成一个数据列表，方便用户直接选择。

```php
<label>
 Sex:
 <input name=sex list=sexes>
 <datalist id=sexes>
  <option value="Female">
  <option value="Male">
 </datalist>
</label>
```

## optgroup {#optgroup}

Optgroup 元素结合select元素使用，将生成列表分组。例如：

```php
<form action="courseselector.dll" method="get">
 <p>Which course would you like to watch today?
 <p><label>Course:
  <select name="c">
   <optgroup label="8.01 Physics I: Classical Mechanics">
    <option value="8.01.1">Lecture 01: Powers of Ten
    <option value="8.01.2">Lecture 02: 1D Kinematics
    <option value="8.01.3">Lecture 03: Vectors
   <optgroup label="8.02 Electricity and Magnestism">
    <option value="8.02.1">Lecture 01: What holds our world together?
    <option value="8.02.2">Lecture 02: Electric Field
    <option value="8.02.3">Lecture 03: Electric Flux
   <optgroup label="8.03 Physics III: Vibrations and Waves">
    <option value="8.03.1">Lecture 01: Periodic Phenomenon
    <option value="8.03.2">Lecture 02: Beats
    <option value="8.03.3">Lecture 03: Forced Oscillations with Damping
  </select>
 </label>
 <p><input type=submit value="Play">
</form>
```

## option {#option}

Option元素为select、optgroup、datalist元素生成列表项目。

## textarea {#textarea}

Textarea 元素表示能输入多段文字的文本框。

```php
<p>如果您有任何意见，烦请告知我们： <textarea cols=80 name=comments></textarea></p>
```

## keygen {#keygen}

Keygen 元素表示密钥生成器，当表单提交时，一个密钥将被提交到服务器。

```php
<form action="" method="post" enctype="multipart/form-data">
        <p><keygen name="key"></p>
        <p><input type=submit value="Submit key..."></p>
</form>
```

## output {#output}

Output 元素表示计算结果或者用户交互的结果。

```php
<form onsubmit="return false" oninput="o.value = a.valueAsNumber + b.valueAsNumber">
        <input name=a type=number step=any> +
        <input name=b type=number step=any> =
        <output name=o for="a b"></output>
    </form>
```

## progress {#progress}

Progress 元素表示进度条。

```php
<section>
        <h2>Task Progress</h2>
        <p>Progress:
            <progress id="p" max=100><span>0</span>%</progress>
        </p>
        <script>
        var progressBar = document.getElementById('p');

        function updateProgress(newValue) {
            progressBar.value = newValue;
            progressBar.getElementsByTagName('span')[0].textContent = newValue;
        }
        updateProgress(50);
        </script>
</section>
```

上述代码将生成一个进度为50\%的进度条。

## meter {#meter}

Meter 元素表示在一定范围内的图形化比值。

```php
<meter min=0 max=20 value=12>12cm</meter>
```

## filedset {#filedset}

Filedset 元素表示表单中的一组表单元素集合。

```php
<fieldset name="numfields">
  <legend> <label>
   <input type=radio checked name=clubtype onchange="form.numfields.disabled = !checked">
   My card has numbers on it
  </label> </legend>
  <div><label>Card number: <input name=clubnum required pattern="[-0-9]+"></label></div>
 </fieldset>
```

## legend {#legend}

Legend 元素在fieldset元素使用，表示fieldset的标题。

