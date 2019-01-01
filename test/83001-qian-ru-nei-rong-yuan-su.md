# 嵌入内容元素 {#嵌入内容元素}

## picture {#picture}

Picture 元素内容包含图片元素，使用source上提供多个来源，以便网页处理设备根据屏幕像素密度、视口大小、图片格式等其他因素选择合适的图片，以便显示。

```php
<picture>
 <source srcset="smaller.jpg" media="(max-width: 768px)">
 <source srcset="default.jpg">
 <img srcset="default.jpg" alt="My default image">
</picture>
```

## img {#img}

Img 元素用来在文档中插入图片。src属性用来指定图片来源，alt属性用来说明图片内容。

## iframe {#iframe}

Iframe 元素生成内嵌框架，引用另外一个网页的内容。src属性用来指定内嵌网页的地址。

```
<iframe src="http://ads.example.com/" width="468" height="60"></iframe>
```

## embed {#embed}

Embed 元素用来嵌入外部非HTML文档内容，比如flash。

### 嵌入flash {#嵌入flash}

尽管flash内容在移动平台日渐式微，但由于已经创作了大量的flash内容，因此，我们也需要掌握在页面中嵌入flash的方法。可通过embed元素嵌入flash，如下：

```php
<embed src="media/css-change-colors.swf" type="application/x-shockwave-flash" width="1024" height="798">
 </embed>
```

embed元素的src属性用来指定flash所在位置，type属性用来声明嵌入的内容为flash，witdh为宽度，height为高度。

## 嵌入视频平台的内容 {#嵌入视频平台的内容}

在国内外，有许多视频网站提供免费视频存储及在线播放服务，如优酷、youtube等等，这些网站几乎都提供将其内容嵌入到其它页面的办法，以优酷为例，嵌入其内容的办法如下：

```php
<embed 
 src="http://player.youku.com/player.php/Type/Folder/Fid/27236393/Ob/1/sid/XMTU3MTQ1MjM3Mg==/v.swf" 
 quality="high" 
 width="480"
 height="400" 
 align="middle" 
 allowScriptAccess="always" 
 allowFullScreen="true"
  mode="transparent" 
  type="application/x-shockwave-flash">
 </embed>
```

究其本质，还是在页面中嵌入flash。

## object {#object}

Object 元素用来嵌入外部对象，插入的对象视为图片元素。

## video {#video}

Video 元素用来插入视频文件。通过src, preload, autoplay, mediagroup, loop, muted, 以及 controls 属性控制视频内容及播放方式。

在HTML5中添加视频和添加音频的方式非常类似。使用video元素，配合src属性，就可以在页面中嵌入视频，其他属性如autoplay、controls、loop以及preload都和audio元素类似。与audio元素不同，vedio元素还可以通过poster属性设定预览图片。例如：

```
<
video
src
=
"
back.ogv
"
controls
poster
=
"
screenshot.jpg
"
>
<
/
video
>
```

.ogv影片格式一个开放标准的视频格式，Firefox、Chrome、Opera支持此格式，但Safari和IE9不支持，支持常用的.mp4视频格式的浏览器有Safari（iPad、Windows、Mac OS）、Chrome、IE9，firefox不支持.mp4格式。

同音频一样，我们可以通过设定不同格式的文件，达到对不同浏览器的兼容：

```
<
video
controls
>
<
source
src
=
"
back.ogv
"
type
=
"
video/ogg
"
>
<
source
src
=
"
back.mp4
"
type
=
"
video/mp4
"
>
<
/
video
>
```

## audio {#audio}

Audio 元素用来插入音频文件。音频文件的播放控制通过属性src, preload, autoplay, mediagroup, loop, muted, 以及 controls 进行设置。

在HTML5之前，在页面中嵌入视音频，绝大多数情况下都需要借助Flash播放器，而HTML5提供了一种快速、简单的添加音频文件的途径，即使用audio元素。和img元素类似，audio元素通过src属性指定文件所在位置，但与img不同的是，audio元素有闭合标签，例如：

```
<
audio
src
=
"
Backroad.ogg
"
>
<
/
audio
>
```

上例的代码将播放当前页面所在目录中的Backroad.ogg音频文件。

Ogg全称是OGG Vorbis， 是一种音频压缩格式，类似于MP3等的音乐格式。但有一点不同的是，它是完全免费、开放和没有专利限制的。MP3格式是受专利保护的，如果你想使用MP3格式发布自己的作品，则需要付给Fraunhofer（发明MP3的公司）专利使用费。

### 设置音频播放属性 {#设置音频播放属性}

audio元素除了具有src属性外，还有其他几个非常实用的属性，包括：

1. **autoplay**
   自动播放当前文件
2. **controls**
   显示音频播放器
3. **loop**
   循环播放
4. **preload**
   预载入音频文件，有三个值：none、auto、metadata，分别表示没有预载入的值、载入所有音频信息值和指定的音频信息值（如作者、时长等等）。

除preload之外，autoplay、 controls 和 loop 都是布尔属性，他们可以不设置值，当它们出现在属性声明中时，它们的值默认为true。

audio元素在默认情况下，并不会显示在页面中。如果autoplay属性出现在audio元素中，则当页面载入的时候，就开始播放音频。如果要显示控制器，则需要添加controls属性，如：

```
<
audio
src
=
"
Backroad.ogg
"
controls
>
<
/
audio
>
```

### 指定多种音频格式 {#指定多种音频格式}

不同浏览器对音频格式的支持是不一致的，绝大多数浏览器都支持常见的音频格式，如.mp3、.wav以及.ogg。HTML5中可以使用source元素，指定多种格式，浏览器会依次判断并读取其支持的格式，例如：

```
<
audio
controls
>
<
source
src
=
"
Backroad.ogg
"
type
=
"
audio/ogg
"
>
<
source
src
=
"
Backroad.mp3
"
type
=
"
audio/mpeg
"
>
<
source
src
=
"
Backroad.wav
"
type
=
"
audio/wav
"
>
<
/
audio
>
```

苹果公司的Safari浏览器不支持ogg格式，但支持MP3格式，因此，我们为同一个音频提供ogg和mp3格式，基本上就能确保大多数情况下音频文件的播放。

## source {#source}

Source 元素的src属性指定媒体文件的来源。

```
<
video
controls
autoplay
>
<
source
src
=
'
video.mp4
'
type
=
'
video/mp4; codecs=
"
avc1.42E01E, mp4a.40.2
"
'
>
<
source
src
=
'
video.ogv
'
type
=
'
video/ogg; codecs=
"
theora, vorbis
"
'
>

 ...

<
/
video
>
```

## track {#track}

Track 元素为媒体文件提供基于时间线的文本信息，如不同语言的字幕。

```
<
video
src
=
"
brave.webm
"
>
<
track
kind
=
subtitles
src
=
brave.en.vtt
srclang
=
en
label
=
"
English
"
>
<
track
kind
=
captions
src
=
brave.en.hoh.vtt
srclang
=
en
label
=
"
English for the Hard of Hearing
"
>
<
track
kind
=
subtitles
src
=
brave.fr.vtt
srclang
=
fr
lang
=
fr
label
=
"
Français
"
>
<
track
kind
=
subtitles
src
=
brave.de.vtt
srclang
=
de
lang
=
de
label
=
"
Deutsch
"
>
<
/
video
>
```

## map {#map}

Map 元素将图片和区域组合起来形成地图。

```
<
IMG
SRC
=
"
/images/menu.gif
"
USEMAP
=
"
#NAV
"
>
<
MAP
NAME
=
"
NAV
"
>
<
P
>
<
A
HREF
=
"
/clothes/
"
>
Clothes
<
/
A
>
<
AREA
ALT
=
"
Clothes
"
COORDS
=
"
0,0,100,50
"
HREF
=
"
/clothes/
"
>
 |

<
A
HREF
=
"
/toys/
"
>
Toys
<
/
A
>
<
AREA
ALT
=
"
Toys
"
COORDS
=
"
0,0,100,50
"
HREF
=
"
/toys/
"
>
 |

<
A
HREF
=
"
/food/
"
>
Food
<
/
A
>
<
AREA
ALT
=
"
Food
"
COORDS
=
"
0,0,100,50
"
HREF
=
"
/food/
"
>
 |

<
A
HREF
=
"
/books/
"
>
Books
<
/
A
>
<
AREA
ALT
=
"
Books
"
COORDS
=
"
0,0,100,50
"
HREF
=
"
/books/
"
>
<
/
MAP
>
```

## area {#area}

Area 元素为图片的指定区域添加超级链接。

## math {#math}

Math 元素用来在HTML文档中插入数学公式。

## svg {#svg}

Svg 元素用来嵌入svg格式图片。

