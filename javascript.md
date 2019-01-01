# JavaScript {#javascript}

JavaScript是一种脚本语言，所谓脚本实际上就是一段嵌入到其他文档中的程序，用来完成特定的功能。JavaScript脚本经常用来检验浏览器，相应用户动作、验证表单数据及实现动态特效等。在网站中，JavaScript扮演的角色逐渐增多，正在蚕食着原本由Flash所占据的领地，如新闻幻灯片、焦点图、事件时间线、新闻地图等等。在Web标准中，行为层的实现目前是以JavaScript脚本为主，可以这样说，JavaScript是事实上的浏览器端脚本。

avaScript 语言正打算在更大的环境中使用，如浏览器,服务端脚本，以及类似环境中。

尽管JavaScript刚开始的设计初衷是作为给非程序人员的脚本语言，但其本质是一门编程语言。[\[15\]](https://yangjh.gitee.io/front-end/References.html#cite-15)

## JavaScript简介 {#javascript简介}

### JavaScript的特点 {#javascript的特点}

JavaScript是一门可以运行在浏览器端的脚本语言。它与浏览器的结合使它成为世界上最为流行的编程语言之一，但它不是所谓的主流编程语言，在对这门语言没有太多了解，甚至对编程都没有什么了解的情况下，用户也能用它解决工作中的一些问题。

JavaScript是事件驱动的语言。当用户在网页中进行某种操作时，就产生了一个“事件”。事件几乎可以是任何事情：单击一个网页元素、鼠标的移动等等均可视为事件。JavaScript是事件驱动的，当事件发生时，它可以对之作出响应。具体如何响应某个时间由编写的事件响应处理程序完成。

JavaScript是一种基于对象的语言，基于对象的语言含有面向对象语言的编程思想，但比面向对象语言更简单。它本身已包含一些创建完成的对象，通常情况下都是使用这些已创建好的对象。

JavaScript是一种容易学习和掌握的编程语言。与其他编程语言相比，JavaScript学习难度较低，学习资源丰富，由于JavaScript大多数情景都是在浏览器端使用，因此，用户可以通过查看源代码来学习，很多网站将所使用的JavaScript脚本都是开放的，可以下载学习并使用。

Javascript是一种跨平台的脚本语言。JavaScript的运行依赖于浏览器本身，与操作环境无关，只要能运行浏览器的计算机，并支持javascript的浏览器就可正确执行。

### JavaScript的用途 {#javascript的用途}

JavaScript可以完成以下任务：

1. JavaScript为HTML提供了一种程序工具，弥补了HTML语言在功能上的局限。HTML只是一种标记语言，它的作用是将网页的内容通过标记组织起来，JavaScript为其提供了实现动态交互和输出的一种途径，它可以很好地结合HTML标记语言实现复杂的应用。
2. JavaScript可以为HTML页面动态添加内容。用户可以传递数据至JavaScript脚本，再由JavaScript修改HTML内容。
3. JavaScript能响应一定的事件。当某些事件发生时，如键入内容、鼠标滑过、页面装载完毕等等，JavaScript都可以根据事件作出响应。
4. JavaScript可以动态地获取和改变HTML的元素属性和CSS属性，从而动态地创建内容和改变内容的显示。
5. JavaScript可以检验数据，这在验证表单时候特别有用，在用户提交数据之前就可以保证数据的正确性，既能减轻服务器压力，又能使用户有更好的体验。
6. JavaScript可以检验用户的浏览器，从而为用户提供更好的页面显示效果。
7. JavaScript可以创建和读取Cookie，根据保留在cookie中的数据，调整页面内容，提供更加个性化的服务。

尽管JavaScript能够完成很多复杂的应用，但由于浏览器安全性的考虑，JavaScript有一些固有的限制，这些限制包括：

1. JavaScript不允许读写客户端文件。唯一的例外是，JavaScript可以读写Cookie文件，但是也有一些限制。这样限制能避免恶意程序传播病毒木马、窃取用户信息。
2. JavaScript不允许写服务器端文件。尽管网页中有大量数据需要从服务器端读取和写入，如用户提交的投票信息、新闻评论、点击量等等，但是JavaScript不允许向服务器写入文件，通常都是利用服务器端脚本，如PHP、ASP程序来完成服务器文件的操作。
3. JavaScript不能从读取已经打开的其它窗口的信息，因此，JavaScript无法知晓浏览当前网页的用户还在访问哪些其它站点。
4. JavaScript不能操纵不是由它打开的窗口，这是为了避免一个站点关闭其他任何站点的窗口，从而独占浏览器，强制用户接受信息。
5. JavaScript调整浏览器窗口的大小和位置时，不能将窗口设置的很小或者移出屏幕之外。

## JavaScript开发环境 {#javascript开发环境}

进行JavaScript的开发，需要开发人员具备以下环境：

1. **文本编辑器**
   JavaScript脚本是纯文本文件，因此，开发人员可选择自己熟悉的文本编辑器，推荐使用Sublime Text编辑器。
2. **浏览器**
   由于JavaScript是网页内容的一部分，要预览脚本的运行效果，自然少不了浏览器，根据项目的不同，开发人员应该选择合适的浏览器，一般而言，至少需要IE、Firefox浏览器。

## Javascript 语言的发展趋势 {#javascript-语言的发展趋势}

### 严格模式 {#严格模式}

JavaScript 语言的设计目的，已经不再局限于浏览器脚本领域，而是向全栈开发前进，因此该语言在未来的前景可谓灿烂，为摆脱早期的设计缺陷， JavaScript 语言推出“严格模式”特性。

严格模式对正常的 JavaScript语义做了一些更改。首先，严格模式消除了一些 JavaScript的静默错误，通过改变它们来抛出错误。 其次，严格的模式修复了 JavaScript引擎难以执行优化的错误：有时候，严格模式代码可以比非严格模式的相同的代码运行得更快。 第三，严格模式禁用了在ECMAScript的未来版本中可能会定义的一些语法。

严格模式代码和非严格模式代码可以共存，但强烈建议初学者一开始就遵守严格模式。开启严格模式很简单，在所有语句之前放一个特定语句`"use strict";`（或`'use strict';`）即可。

Mozilla官方建议，最好还是按一个个函数去开启严格模式（至少在学习的过渡期要这样做），您可以将整个脚本的内容用一个函数包括起来，然后在这个函数中使用严格模式。

### ES6 {#es6}

## JavaScript学习资源 {#javascript学习资源}

尽管网络上有丰富的学习资源，但其良莠不齐，因此学习者应该有权威准确、更新及时的参考手册，推荐以下学习资源：

1. [https://developer.mozilla.org/zh-CN/docs/Web/JavaScript](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript)
2. 《精通JavaScript》
3. 《JavaScript DOM编程艺术》
4. 《JavaScript高级程序设计》
5. 《JavaScript语言精粹》
6. 《你不知道的JavaScript》
7. 《JavaScript设计模式》
8. 《JavaScript权威指南》
9. [JavaScript知识在线测试](https://www.nowcoder.com/intelligentTest)



