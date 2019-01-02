# 11、脚本元素

脚本元素可为文档增加用户交互性。

## script <a id="script"></a>

元素script能为HTML文档包含动态脚本和数据块，包含在script元素中的内容不会直接显示给用户。

当使用script元素包含动态脚本时，脚本内容既可以直接嵌入在行内，也可以通过scr属性导入外部独立的脚本文件。

script元素除全局性属性之外，还拥有以下几个属性：

1. **src**

   外部脚本文件的地址

2. **type**

   内嵌资源的类型。type的默认值是"text/javascript"。如果脚本语言不是JavaScript，则必须指定type的值。

3. **charset**

   外部脚本文件的字符编码方式

4. **async**使浏览器可以尽快地执行脚本，而不用在下载脚本时阻塞文档解析（异步）。在不支持async的浏览器中，通过动态创建`<script>`元素并把它插入文档中，来实现脚本的异步载入和执行。
5. **defer**使得浏览器延迟脚本的执行，直到文档的载入和解析完成，并可以操作。
6. **crossorigin** 设置元素处理跨域请求的方式。

## noscript <a id="noscript"></a>

Noscript 元素当浏览器支持脚本时，其包含的内容不被显示；而当浏览器禁用脚本或者不支持脚本时，将会显示其内容。

## template <a id="template"></a>

Template 表示HTML模版片段，结合JavaScript能生成基于模版的动态内容。

## canvas <a id="canvas"></a>

Canvas 元素表示可实时生成内容的画布，结合JavaScript，可生成动画、背景、游戏场景等等图片。

