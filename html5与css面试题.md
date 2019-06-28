## 浏览器/html/css面试题

##### 1.什么是盒模型

SS盒子模型就是在网页设计中经常用到的CSS技术所使用的一种思维模型。
　　网页设计中常听的属性名：内容(content)、填充(padding)、边框(border)、边界(margin)， CSS盒子模式都具备这些属性。
　　这些属性可以把它转移到日常生活中的盒子（箱子）上来理解，日常生活中所见的盒子也就是能装东西的一种箱子，也具有这些属性，所以叫它盒子模式。
　　每个盒子都有：边界、边框、填充、内容四个属性；
　　每个属性都包括四个部分：上、右、下、左；这四部分可同时设置，也可分别设置；里的抗震辅料厚度，而边框有大小和颜色之分，又可以理解为生活中所见盒子的厚度以及这个盒子是用什么颜色材料做成的，边界就是该盒子与其它东西要保留多大距离。

把标签（例如div）想象成一个盒子，它有:外边距(margin)、边框(border)、内边距(padding)、内容(content)四个属性;

让我们俯视这个盒子，它有上下左右四条边，所以每个属性除了内容(content)，都包括四个部分:上下左右;这四部分可同时设置，也可分别设置;内边距**(padding)**可以理解为盒子里装的东西和边框的距离，而边框**(border)**有厚薄和颜色之分，内容**(content)**就是盒子中间装的东西，外边距**(margin)**就是边框外面自动留出的一段空白，控制盒子与盒子之间的间隙。

##### 2.行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？行内元素和块级元素有什么区别？

首先：CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。

```
（1）行内元素有：a b span img input select strong（强调的语气）
（2）块级元素有：div ul ol li dl dt dd h1 h2 h3 h4…p
（3）常见的空元素：
    <br> <hr> <img> <input> <link> <meta>
    鲜为人知的是：
    <area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>
```

##### 3.简述src和href的区别

src用于替换当前元素，href用于在当前文档和引用资源之间确立联系。

##### 4.什么是css Hack

CSS hack**由于不同厂商的浏览器**，比如Internet Explorer,Safari,Mozilla Firefox,Chrome等，或者是同一厂商的浏览器的不同版本，如IE6和IE7，**对CSS的解析认识不完全一样，因此会导致生成的页面效果不一样**，得不到我们所需要的页面效果。 **这个时候我们就需要针对不同的浏览器去写不同的CSS**，**让它能够同时兼容不同的浏览器**，能在不同的浏览器中也能得到我们**想要的页面效果**。
简单的说，CSS hack的目的就是使你的CSS代码兼容不同的浏览器。当然，我们也可以反过来利用CSS hack为不同版本的浏览器定制编写不同的CSS效果。

##### 5.什么叫优雅降级和渐进增强

**什么是渐进增强、优雅降级？**

　　渐进增强 progressive enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

　　优雅降级 graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。　

**区别：**

　　优雅降级是从复杂的现状开始，并试图减少用户体验的供给，

　　而渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要。

　　降级（功能衰减）意味着往回看；而渐进增强则意味着朝前看，同时保证其根基处于安全地带。

 

**“优雅降级”观点**

“优雅降级”观点认为应该针对那些最高级、最完善的浏览器来设计网站。而将那些被认为“过时”或有功能缺失的浏览器下的测试工作安排在开发周期的最后阶段，并把测试对象限定为主流浏览器（如 IE、Mozilla 等）的前一个版本。

在这种设计范例下，旧版的浏览器被认为仅能提供“简陋却无妨 (poor, but passable)” 的浏览体验。你可以做一些小的调整来适应某个特定的浏览器。但由于它们并非我们所关注的焦点，因此除了修复较大的错误之外，其它的差异将被直接忽略。

 

**“渐进增强”观点**

“渐进增强”观点则认为应关注于内容本身。

内容是我们建立网站的诱因。有的网站展示它，有的则收集它，有的寻求，有的操作，还有的网站甚至会包含以上的种种，但相同点是它们全都涉及到内容。这使得“渐进增强”成为一种更为合理的设计范例。这也是它立即被 Yahoo! 所采纳并用以构建其“分级式浏览器支持 (Graded Browser Support)”策略的原因所在。

##### 6.px和em的区别

px、em、rem都是计量单位，都能表示尺寸，但是有有所不同，而且其各有各的优缺点。

Px表示“绝对尺寸”（并非真正的绝对），实际上就是css中定义的像素（此像素与设备的物理像素有一定的区别，后续详细说明见文末说明1），利用px设置字体大小及元素宽高等比较稳定和精确。Px的缺点是其不能适应浏览器缩放时产生的变化，因此一般不用于响应式网站。

em表示相对尺寸，其相对于当前对象内文本的font-size（如果当前对象内文本的font-size计量单位也是em，则当前对象内文本的font-size的参考对象为父元素文本font-size）。使用em可以较好的相应设备屏幕尺寸的变化，但是在进行元素设置时都需要知道父元素文本的font-size及当前对象内文本的font-size，如有遗漏可能会导致错误。

rem也表示相对尺寸，其参考对象为根元素<html>的font-size，因此只需要确定这一个font-size。

##### 7.HTML5 为什么只写需要写！doctype

如果没有写doctype  则会出现怪异盒模型

也就是浏览器会出现各种的不兼容

HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；

而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

##### 8.Http的状态码有哪些


HTTP状态码的英文为HTTP Status Code。下面是常见的HTTP状态码：

200 – 请求成功

301 – 资源(网页等)被永久转移到其它URL

404 – 请求的资源(网页等)不存在

500 – 内部服务器错误

##### 9.一次完整的HTTP事务是怎么一个过程

1、域名解析

2、发起TCP的三次握手

3、建立TCP连接后发起http请求

4、服务器端响应http请求，浏览器得到html码

5、浏览器解析html代码，并请求html代码中的资源

6、浏览器对页面进行渲染并呈现给客户

##### 10.HTTPS是如何实现加密

HTTPS，在我的概念中就是更安全；

HTTP 是一种超文本传输协议，它是无状态的、简单快速的、基于 TCP 的可靠传输协议。

##### 11.浏览器是如何渲染页面的

1. 处理HTML标记并构建DOM树
2. 处理CSS标记并构建CSSOM树
3. 将DOM与CSSOM合并成一个渲染树
4. 根据渲染树来布局，计算每个节点的布局信息
5. 将各个节点绘制到屏幕上

##### 12.浏览器的内核有哪些？分别有什么代表的浏览器

IE	Trident	IE、猎豹安全、360极速浏览器、百度浏览器

firefox	Gecko	可惜这几年已经没落了，打开速度慢、升级频繁、猪一样的队友flash、神一样的对手chrome。

Safari	webkit	从Safari推出之时起，它的渲染引擎就是Webkit，一提到 webkit，首先想到的便是 chrome，可以说，chrome 将 Webkit内核 深入人心，殊不知，Webkit 的鼻祖其实是 Safari。

chrome	Chromium/Blink	在 Chromium 项目中研发 Blink 渲染引擎（即浏览器核心），内置于 Chrome 浏览器之中。Blink 其实是 WebKit 的分支。大部分国产浏览器最新版都采用Blink内核。二次开发

Opera	blink	现在跟随chrome用blink内核。作

##### 13.页面导入时，使用link和@import有什么区别

1）link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;

（2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
（3）import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;

##### 14.如何优化图像，图像格式的区别

存jpg的格式，有品质可以选择，100%为最佳品质，越向下，图像质量越差。文件体积越小，
还可存gif格式，GIF只有256个颜色，可以选择8、32、64个颜色输出，也能减小文件体积，但图像质量也会变差

##### 15.列举你了解Html5. Css3 新特性

### html5:

- 用于绘画的 canvas 元素 以及SVG
- 用于媒介回放的 video 和 audio 元素
- 拖拽(Drag 和 drop) 地理定位(Geolocation)
- 对本地离线存储的更好的支持
  localStorage - 没有时间限制的数据存储
  sessionStorage - 针对一个 session 的数据存储
  之前，这些都是由 cookie 完成的。但是 cookie 不适合大量数据的存储，因为它们由每个对服务器的请求来传递，这使得 cookie 速度很慢而且效率也不高。
  在 HTML5 中，数据不是由每个服务器请求传递的，而是只有在请求时使用数据。它使在不影响网站性能的情况下存储大量数据成为可能。
  对于不同的网站，数据存储于不同的区域，并且一个网站只能访问其自身的数据。)
- 新的特殊内容元素，比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search
- 新的 form 属性：
  autocomplete
  novalidate
- 新的 input 属性：
  autocomplete
  autofocus
  form
  form overrides (formaction, formenctype, formmethod, formnovalidate, formtarget)
  height 和 width
  list
  min, max 和 step
  multiple
  pattern (regexp)
  placeholder
  required
- 语义元素：有利于搜索引擎优化和快速查找
  HTML5 添加了很多语义元素如下所示：
  标签 描述

```
<article>   定义页面独立的内容区域。
<aside>   定义页面的侧边栏内容。
<bdi>    允许您设置一段文本，使其脱离其父元素的文本方向设置。
<command>   定义命令按钮，比如单选按钮、复选框或按钮
<details>   用于描述文档或文档某个部分的细节
<dialog>    定义对话框，比如提示框
<summary>   标签包含 details 元素的标题
<figure>    规定独立的流内容（图像、图表、照片、代码等等）
<figcaption>    定义 <figure> 元素的标题
<footer>    定义 section 或 document 的页脚。
<header>    定义了文档的头部区域
<mark>  定义带有记号的文本。
<meter> 定义度量衡。仅用于已知最大和最小值的度量。
<nav>   定义导航链接的部分。
<progress>  定义任何类型的任务的进度。
<ruby>  定义 ruby 注释（中文注音或字符）。
<rt>    定义字符（中文注音或字符）的解释或发音。
<rp>    在 ruby 注释中使用，定义不支持 ruby 元素的浏览器所显示的内容。
<section>   定义文档中的节（section、区段）。
<time>  定义日期或时间。
<wbr>   规定在文本中的何处适合添加换行符。
```

CSS3实现圆角（border-radius），阴影（box-shadow），
对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）
transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);// 旋转,缩放,定位,倾斜
增加了更多的CSS选择器  多背景 rgba
在CSS3中唯一引入的伪元素是 ::selection.
媒体查询，多栏布局
border-image

##### 16.可以通过哪些方法优化css3 animation渲染

**创建动画**：@keyframes规则。

创建动画 使用百分比定义动画

将动画**绑定**到选择器：

规定动画开始时的等待时间：

animation-delay：时间；可以为秒、毫秒2s，2ms。

播放次数：animation-iteration-count：次数；永久播放的值取infinite。

动画速度曲线：

animation-timing-function：变化类型；变化类型有：linear 匀速；ease-in 开始慢；ease-out 结束慢；ease 动画有一个缓慢的开始，然后快，结束慢。



##### 17.列举几个前端性能方面的优化

###### 网络方面

web应用，总是会有一部分的时间浪费在网络连接和资源下载方面。往往建立一次网络连接是需要时间成本的。而且浏览器同一时间所发送的网络请求数是有限的。所以，这个层面的优化可以从「减少请求数目」开始：

1. ###### **减少http请求**：在YUI35规则中也有提到，主要是优化js、css和图片资源三个方面，因为html是没有办法避免的。因此，我们可以做一下的几项操作：

   - 合并js文件
   - 合并css文件
   - 雪碧图的使用(css sprite)
   - 使用base64表示简单的图片

   上述四个方法，前面两者我们可以使用webpack之类的打包工具进行打包；雪碧图的话，也有专门的制作工具；图片的编码是使用base64的，所以，对于一些简单的图片，例如空白图等，可以使用base64直接写入html中。

回到之前网络层面的问题，除了减少请求数量来加快网络加载速度，往往整个资源的体积也是，平时我们会关注的方面。

1. **减小资源体积**：可以通过以下几个方面进行实施：

   - gzip压缩
   - js混淆
   - css压缩
   - 图片压缩

   gzip压缩主要是针对html文件来说的，它可以将html中重复的部分进行一个打包，多次复用的过程。js的混淆可以有简单的压缩(将空白字符删除)、丑化(丑化的方法，就是将一些变量缩小)、或者可以使用php对js进行混淆加密。css压缩，就是进行简单的压缩。图片的压缩，主要也是减小体积，在不影响观感的前提下，尽量压缩图片，使用png等图片格式，减少矢量图、高清图等的使用。这样子的做法不仅可以加快网页显示，也能减少流量的损耗。

除了以上两部分的操作之外，在网络层面我们还需要做好缓存工作。真正的性能优化来说，缓存是效率最高的一种，往往缩短的加载时间也是最大的。

1. **缓存**：可以通过以下几个方面来描述：

   - DNS缓存
   - CDN部署与缓存
   - http缓存

   由于浏览器会在DNS解析步骤中消耗一定的时间，所以，对于一些高访问量网站来说，做好DNS的缓存工作，就会一定程度上提升网站效率。CDN缓存，CDN作为静态资源文件的分发网络，本身就已经提升了，网站静态资源的获取速度，加快网站的加载速度，同时也给静态资源做好缓存工作，有效的利用已缓存的静态资源，加快获取速度。http缓存，也是给资源设定缓存时间，防止在有效的缓存时间内对资源进行重复的下载，从而提升整体网页的加载速度。

其实，网络层面的优化还有很多，特别是针对于移动端页面来说。众所周知，移动端对于网络的敏感度更加的高，除了目前的4G和WIFI之外，其他的移动端网络相当于弱网环境，在这种环境下，资源的缓存利用是相当重要的。而且，减少http的请求次数，也是至关重要的，移动端弱网环境下，对于http请求的时间也会增加。所以，我们可以看一下我们在移动端网络方面可以做的优化：

1. **移动端优化**：使用以下几种方式来加快移动端网络方面的优化：

   - 使用长cache，减少重定向
   - 首屏优化，保证首屏加载数据小于14kb
   - 不滥用web字体

   「使用长cache」，可以使得移动端的部分资源设定长期缓存，这样可以保证资源不用向服务器发送请求，来比较资源是否更新，从而避免304的情况。304重定向，在PC端或许并不会影响网页的加载速度，但是，在移动端网络不稳定的前提下，多一次请求，就多了一部分加载时间。「首屏优化」，对于移动端来说是至关重要的。2s时间是用户的最佳体验，一旦超出这个时间，将会导致用户的流失。所以，针对移动端的网络情况，不可能在这么短时间内加载完成所有的网页资源，所以我们必须保证首屏中的内容被优先显示出来，而且基于TCP的慢启动和拥塞控制，第一个14kb的数据是非常重要的，所以需要保证首部加载数据能够小于14kb。「不滥用web字体」，web字体的好处就是，可以代替某些图片资源，但是，在移动端过多的web字体的使用，会导致页面资源加载的繁重，所以，慎用web字体

   **移动端优化**：

   - 长列表滚动优化
   - 函数防抖和函数节流
   - 使用touchstart、touchend代替click
   - HTML的viewport设置
   - 开启GPU渲染加速

   **DOM操作优化**：

   - 避免在document上直接进行频繁的DOM操作
   - 使用classname代替大量的内联样式修改
   - 对于复杂的UI元素，设置position为absolute或fixed
   - 尽量使用css动画
   - 使用requestAnimationFrame代替setInterval操作
   - 适当使用canvas
   - 尽量减少css表达式的使用
   - 使用事件代理

   

   **优化网页渲染**：

   - css的文件放在头部，js文件放在尾部或者异步
   - 尽量避免內联样式

##### 18.如何实现同一个浏览器多个标签页之间的通信

使用websocket协议、通过localstorage、以及使用html5浏览器的新特性SharedWorker。

websocket这里先不介绍了,全双工(full-duplex)通信自然可以实现多个标签页之间的通信，相信网上通过websocket实现聊天室的教程也不少，我自己也用socket.io写了一个[在线聊天室](https://link.jianshu.com?t=http%3A%2F%2F101.200.35.148%2Fdist%2F%23%2FcheatRoom) 

接下来会介绍另外两个方法：监听localstorage和使用SharedWorker

#### webworker

- 我们都知道JavaScript是**单线程**的，但是浏览器是拥有过个线程的比如：gui渲染线程、JS引擎线程、事件触发线程、异步http请求线程。
- webworker作为浏览器的一个新特性，可以提供一个**额外的线程**来执行一些js代码，并且不会影响到浏览器用户界面。
- 应用场景：比如页面中包含耗时较大的算法代码时，就会阻塞线程影响浏览器渲染等等。这时候就可把耗时代码，放到webworker(另一个线程)中执行。
- 注意，这种多线程能力不是JavaScript语言原生具有的，而是浏览器宿主环境提供的。
- 普通的webworker直接使用`new Worker()`即可创建，这种webworker是**当前页面**专有的。然后还有种共享worker(SharedWorker)，这种是可以多个标签页、iframe共同使用的，接下来介绍如何使用SharedWorker实现标签页之间的通信。

##### 19.浏览器的存储技术有哪些

cookie：放在http请求头中，伴随数据传输而传输，数据传输大小有限制，有过期时间 

  localstorage：存储在本地，不会伴随数据传输，生命周期为永久 

  sessionstorage：浏览器中，浏览器关闭则消失，即使在同源浏览器中也不能共享 

  userdata：ie中用于浏览器存储技术 

  globalstorage：ff中用于浏览器存储

##### 20.css定位方式

##### 21.尽可能多的写出浏览器兼容性问题

*兼容性处理要点**
1、DOCTYPE 影响 CSS 处理 
2、FF: 设置 padding 后， div 会增加 height 和 width， 但 IE 不会， 故需要用 !important 多设一个 height 和 width 
3、FF: 支持 !important， IE 则忽略， 可用 !important 为 FF 特别设置样式 
4、div 的垂直居中问题: vertical-align:middle; 将行距增加到和整个DIV一样高 line-height:200px; 然后插入文字，就垂直居中了。缺点是要控制内容不要换行 
5、在mozilla firefox和IE中的BOX模型解释不一致导致相差2px解决方法： 
div{margin:30px!important;margin:28px;} 
注意这两个margin的顺序一定不能写反，!important这个属性IE不能识别，但别的浏览器可以识别。所以在IE下其实解释成这样： 
div{maring:30px;margin:28px} 
重复定义的话按照最后一个来执行，所以不可以只写margin:XXpx!important; 
*浏览器差异 1、ul和ol列表缩进问题**
消除ul、ol等列表的缩进时，样式应写成：list-style:none;margin:0px;padding:0px; 
其中margin属性对IE有效，padding属性对FireFox有效。 
[注] 经验证，在IE中，设置margin:0px可以去除列表的上下左右缩进、空白以及列表编号或圆点，设置padding对样式没有影响；在 Firefox 中，设置margin:0px仅仅可以去除上下的空白，设置padding:0px后仅仅可以去掉左右缩进，还必须设置list- style:none才 能去除列表编号或圆点。也就是说，在IE中仅仅设置margin:0px即可达到最终效果，而在Firefox中必须同时设置margin:0px、 padding:0px以及list-style:none三项才能达到最终效果。 
*2、CSS透明问题**
IE：filter:progid:DXImageTransform.Microsoft.Alpha(style=0,opacity=60)。 
FF：opacity:0.6。 
[注] 最好两个都写，并将opacity属性放在下面。 
*3、CSS圆角问题**
IE：ie7以下版本不支持圆角。 
FF： -moz-border-radius:4px，或者-moz-border-radius-topleft:4px;-moz- border- radius-topright:4px;-moz-border-radius-bottomleft:4px;-moz- border- radius- bottomright:4px;。 
[注] 圆角问题是CSS中的经典问题，建议使用JQuery框架集来设置圆角，让这些复杂的问题留给别人去想吧。不过jQuery的圆角只看到支持整个区域的圆角，没有支持边框的圆角，不过这个边框的圆角可以通过一些简单的手段来实现，下次有机会介绍下。 
*4、cursor:hand VS cursor:pointer**
问题说明：firefox不支持hand，但ie支持pointer ，两者都是手形指示。 
解决方法：统一使用pointer

字体大小定义不同**
对字体大小small的定义不同，Firefox中为13px，而IE中为16px，差别挺大。 
解决方法：使用指定的字体大小如14px。 
并列排列的多个元素（图片或者链接）的div和div之间，代码中的空格和回车在firefox中都会被忽略，而IE中却默认显示为空格（约3px）。 
*6、CSS双线凹凸边框**
IE：border:2px outset;。 
FF： -moz-border-top-colors: #d4d0c8 white;-moz-border-left-colors: #d4d0c8 white;-moz-border-right-colors:#404040 #808080;-moz-border-bottom-colors:#404040 #808080; 
*浏览器bug**
*1、IE的双边距bug**
设置为float的div在ie下设置的margin会加倍。这是一个ie6都存在的bug。 
解决方案：在这个div里面加上display:inline; 

##### 22.垂直上下居中的方法

##### 23.响应式布局原理

响应式布局指的是同一页面在不同屏幕尺寸下有不同的布局。传统的开发方式是PC端开发一套，手机端再开发一套，而使用响应式布局只要开发一套就够，缺点就是`CSS`比较重。

`CSS3`媒体查询可以让我们针对不同的媒体类型定义不同的样式，当重置浏览器窗口大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面。

通过百分比单位，可以使得浏览器中组件的宽和高随着浏览器的高度的变化而变化，从而实现响应式的效果。Bootstrap里面的栅格系统就是利用百分比来定义元素的宽高，`CSS3`支持最大最小高，可以将百分比和`max(min)`一起结合使用来定义元素在不同设备下的宽高

`REM`是`CSS3`新增的单位，并且移动端的支持度很高，Android2.x+,ios5+都支持。`rem`单位都是相对于根元素html的`font-size`来决定大小的,根元素的`font-size`相当于提供了一个基准，当页面的size发生变化时，只需要改变`font-size`的值，那么以`rem`为固定单位的元素的大小也会发生响应的变化。 因此，如果通过`rem`来实现响应式的布局，只需要根据视图容器的大小，动态的改变`font-size`即可（而`em`是相对于父元素的）。

`css3`中引入了一个新的单位`vw/vh`，与视图窗口有关，`vw`表示相对于视图窗口的宽度，`vh`表示相对于视图窗口高度

**总结**：响应式布局的实现可以通过媒体查询+`px`,媒体查询+百分比，媒体查询+`rem`+`js`,`vm/vh`,`vm/vh` +`rem`这几种方式来实现。但每一种方式都是有缺点的，媒体查询需要选取主流设备宽度尺寸作为断点针对性写额外的样式进行适配，但这样做会比较麻烦，只能在选取的几个主流设备尺寸下呈现完美适配，另外用户体验也不友好，布局在响应断点范围内的分辨率下维持不变，而在响应断点切换的瞬间，布局带来断层式的切换变化，如同卡带的唱机般“咔咔咔”地一下又一下。通过百分比来适配首先是计算麻烦，第二各个属性中如果使用百分比，其相对的元素的属性并不是唯一的，这样就造成我们使用百分比单位容易使布局问题变得复杂。通过采用`rem`单位的动态计算的弹性布局，则是需要在头部内嵌一段脚本来进行监听分辨率的变化来动态改变根元素字体大小，使得`CSS`与`JS` 耦合了在一起。通过利用纯`css`视口单位实现适配的页面，是既能解决响应式断层问题，又能解决脚本依赖的问题的，但是兼容性还没有完全能结构接受。

##### 25.清除浮动的方法

1）给父元素设置高度（推荐指数：★ ★）
既然没了高度就人为设置一个
2）父元素浮动（推荐指数：0）
这种方法不推荐，都浮动后，不利于父级的布局。
3）display:inline-block（推荐指数：★ ★）
不采用float的方法，用行内元素布局，同样可以将多个盒子同行排列，但是会有一些不知所谓的边距。
后面3种方法则是采取清除浮动的方法
4）overflow：hidden；（推荐指数：★ ★★ ★）
overflow:hidden;
float：left;

zoom:1用于兼容IE6。

##### 26.http协议和tcp协议

　HTTP协议是hypertexttransferprotocol（超文本传输协议）的简写，它是TCP/IP协议的一个应用层协议，用于定义WEB浏览器服务器之间交换数据的过程，客户端连上web服务器后，若想获得web服务器中的某个资源，需遵守一定的通讯格式，HTTP协议用于定义客户端与web服务器通讯的格式。

　TCP/IP是一个大集合，所以统称TCP/IP协议。

　　TCP/IP分为四个层，每一层分一个职责，那个层除了问题直接维护那个层即可。

　1：链路层

　　2：网络层

　　3：传输层

　　4：应用层



##### 27.刷新页面，js请求一般会有哪些地方有缓存处理

DNS缓存：短时间内多次访问某个网站，在限定时间内，不用多次访问DNS服务器。

CDN缓存：内容分发网络（人们可以在就近的代售点取火车票了，不用非得到火车站去排队）

浏览器缓存：浏览器在用户磁盘上，对最新请求过的文档进行了存储。

服务器缓存：将需要频繁访问的Web页面和对象保存在离用户更近的系统中，当再次访问这些对象的时候加快了速度。

##### 28.如何对网站的文件和资源进行优化

.文件合并（目的是减少http请求）：使用css sprites合并图片，一个网站经常使用小图标和小图片进行美化，但是很遗憾这些小图片占用了大量的HTTP请求，因此可以采用sprites的方式把所有的图片合并成一张图片 ，可以通过相关工具在线合并，也可以在ps中合并。

2.使用CDN（内容分发网络）加速，降低通信距离。

3.缓存的使用，添加Expire/Cache-Control头。

4.启用Gzip压缩文件。

压缩js和css可以通过服务器动态脚本进行也可以更简单的使用apache服务器可以在网站根目录 .htaccess 中加入以下代码AddOutputFilterByType DEFLATE text/html text/css text/plain text/xml application/x-javascript application/json

Header append Vary Accept-Encoding

　　这段代码的意思是调用服务器的压缩模块对以上文件输出之前进行GZIP压缩，gzip的压缩之后所有文件都应该能减少30%以上的体积。特别是对于大量使用js的博客有了gzip保驾护航之后速度能提高不少。

5.将css放在页面最上面。

6.将script放在页面最下面。

7.避免在css中使用表达式。

8.将css, js都放在外部文件中。

9.减少DNS查询。

10.文件压缩：最小化css, js，减小文件体积。

11.避免重定向。

12.移除重复脚本。

13.配置实体标签ETag。

14.使用AJAX缓存，让网站内容分批加载，局部更新。

##### 29.你对网页标准和W3C重要性的理解

[万维网联盟](http://baike.baidu.com/view/80669.htm)（外语缩写：W3C）标准不是某一个标准，而是一系列标准的集合。网页主要由三部分组成：结构（Structure）、表现（Presentation）和行为（Behavior）。

对应的标准也分三方面：结构化标准语言主要包括[XHTML](http://baike.baidu.com/view/15906.htm)和[XML](http://baike.baidu.com/view/63.htm)，表现标准语言主要包括[CSS](http://baike.baidu.com/view/15916.htm)，行为标准主要包括对象模型（如W3C DOM）、ECMA[Script](http://baike.baidu.com/view/266997.htm)等。这些标准大部分由W3C起草和发布，也有一些是其他标准组织制订的标准，比如[ECMA](http://baike.baidu.com/view/786648.htm)（European Computer Manufacturers Association）的ECMAScript标准。

##### 30.Http和https的区别

1、https协议需要到ca申请证书，一般免费证书较少，因而需要一定费用。

2、http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。

3、http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。

4、http的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。31.data-属性的作用

##### 32.如何让Chrome浏览器显示小于12px的文字

 -webkit-transform: scale(0.90); /* Safari 和 Chrome */
-webkit-transform-origin:0 0;   /* Safari 和 Chrome */

##### 33.哪些操作会引起页面回流（Reflow）

① 改变窗口大小

② font-size大小改变

③ 增加或者移除样式表

④ 内容变化（input中输入文字会导致）

⑤ 激活CSS伪类（:hover）

⑥ 操作class属性，新增或者减少

⑦ js操作dom

⑧ offset相关属性计算

⑨ 设置style的值

reflow与repaint是减缓js的几大主要原因，尤其是reflow更是性能杀手，所以我们应该想法避免。

##### 34.CSS预处理器的比较less sass

、主要区别是他们的实现方式不同，LESS是基于JavaScript运行,所以LESS是在客户端处理。

另一方面，Sass是基于Ruby的，是在服务器端处理的。很多开发者不选择LESS是因为LESS输出修改过的CSS到浏览器需要依赖于Javascript引擎，而Javascript引擎需要额外的时间来处理代码。关于这个有很多种方式，我选择的是只在开发环节使用LESS。一旦开发完成，我就复制粘贴LESS输出的到一个压缩器，然后到一个单独的CSS文件来替代LESS文件。另一种方式是使用[LESS APP](http://incident57.com/less)来编译和压缩你的LESS文件。两种方式都将是最小化你的样式输出，从而避免由于用户的浏览器不支持Javascript而可能引起的任何问题。尽管这不大可能，但终归是有可能的。

##### 35.如何实现页面每次打开时清除本页缓存

1） 用HTML标签设置HTTP头信息

<meta http-equiv="Pragma" content="no-cache">
header("Cache-Control: no-cache, must-revalidate")
<meta http-equiv="Cache-Control" content="no-cache">
<meta http-equiv="Expires"  content="0">
说明：HTTP头信息“Expires”和“Cache-Control”为应用程序服务器提供了一个控制浏览器和代理服务器上缓存的机制。HTTP头信息Expires告诉代理服务器它的缓存页面何时将过期。HTTP1.1规范中新定义的头信息Cache-Control可以通知浏览器不缓存任何页面。当点击后退按钮时，浏览器重新访问服务器已获取页面。如下是使用Cache-Control的基本方法：

　　1) no-cache:强制缓存从服务器上获取新的页面

　　2) no-store: 在任何环境下缓存不保存任何页面

hTTP1.0规范中的Pragma:no-cache等同于HTTP1.1规范中的Cache-Control:no-cache，同样可以包含在头信息中。

（2） 在需要打开的url后面增加一个随机的参数：

增加参数前：url=test/test.jsp

增加参数后：url=test/test.jsp?ranparam=random()

说明：因为每次请求的url后面的参数不一样，相当于请求的是不同的页面，用这样的方法来曲线救国，清除缓存

##### 36.什么是Virtual DOM,为何要用Virtual DOM

virtual dom就是原生dom在内存中的js对象映射，但不是完全复制，它比真实dom节点在属性上简化了，也就是说是更加轻量级，相当于是数据和原生dom的一层缓存。

初始渲染：Virtual DOM > 脏检查 >= 依赖收集

小量数据更新：依赖收集 >> Virtual DOM + 优化 > 脏检查（无法优化） > Virtual DOM无优化

大量数据更新：脏检查 + 优化 >= 依赖收集 + 优化 > Virtual DOM（无法/无需优化）>> MVVM 无优化。

##### 37.伪元素和伪类的区别

> 伪类存在的意义是为了通过选择器找到那些不存在与DOM树中的信息以及不能被常规CSS选择器获取到的信息。

> 伪类由**一个**冒号`:`开头，冒号后面是伪类的名称和包含在圆括号中的可选参数。

> 任何常规选择器可以再任何位置使用伪类。伪类语法不区别大小写。一些伪类的作用会互斥，另外一些伪类可以同时被同一个元素使用。并且，为了满足用户在操作DOM时产生的DOM结构改变，伪类也可以是动态的。

##### 38.http的几种请求方法和区别

HTTP协议是一个广泛应用的Internet协议。在其中有8个不同的请求方法：

1. GET
2. POST
3. HEAD
4. PUT
5. DELETE
6. OPTIONS
7. TRACE
8. CONNECT

这8个方法中GET和POST最常见

##### 39.前端需要注意哪些SEO

1、 合理的title，description，keyswords 搜索引擎对这三项的权重逐个减小，title 值强调重点即可，重要的关键

词出现不要超过两次，而且要靠前。

2 、不同页面的tilte要有所不同；description把页面的内容高度概括，长度合适，不可过分堆叠关键词，不同页面

description有所不同。keyswords列举出重要的关键词即可。

3、语义化的HTML代码，符合W3C 规范：语义化代码有利于搜索引擎理解网页。

4 、重要的内容HTML代码放在前面：搜索引擎抓取HTML 的顺序是从上到下，有的搜索引擎对抓取长度有限制，保

证重要内容一定会被抓取。

5 、重要的内容不要用js输出，爬虫不会执行js获取内容。

6 、尽量少用iframe ，搜索引擎不会抓取iframe中的内容。

7 、非装饰的图片必须加alt 。

8 、提高网站速度：网站速度是搜索引擎排序的一个重要指标。

##### 40.的title和alt有什么区别

[alt](https://www.baidu.com/s?wd=alt&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)是当你图片显示不出显示的文字，title是你用鼠标放到图片上显示的文字，最好是两个区别开来 

##### 41.从浏览器地址栏输入url到显示页面的步骤

1. 在浏览器地址栏输入URL

2. 浏览器查看缓存，如果请求资源在缓存中并且新鲜，跳转到转码步骤

   1. 如果资源未缓存，发起新请求

   2. 如果已缓存，检验是否足够新鲜，足够新鲜直接提供给客户端，否则与服务器进行验证。

   3. 检验新鲜通常有两个HTTP头进行控制

      ```
      Expires
      ```

      和

      ```
      Cache-Control
      ```

      ：

      - HTTP1.0提供Expires，值为一个绝对时间表示缓存新鲜日期
      - HTTP1.1增加了Cache-Control: max-age=,值为以秒为单位的最大新鲜时间

3. 浏览器解析URL获取协议，主机，端口，path

4. 浏览器组装一个HTTP（GET）请求报文

5. 浏览器获取主机ip地址，过程如下：

   1. 浏览器缓存
   2. 本机缓存
   3. hosts文件
   4. 路由器缓存
   5. ISP DNS缓存
   6. DNS递归查询（可能存在负载均衡导致每次IP不一样）

6. 打开一个socket与目标IP地址，端口建立TCP链接，三次握手如下：

   1. 客户端发送一个TCP的SYN=1，Seq=X的包到服务器端口
   2. 服务器发回SYN=1， ACK=X+1， Seq=Y的响应包
   3. 客户端发送ACK=Y+1， Seq=Z

7. TCP链接建立后发送HTTP请求

8. 服务器接受请求并解析，将请求转发到服务程序，如虚拟主机使用HTTP Host头部判断请求的服务程序

9. 服务器检查HTTP请求头是否包含缓存验证信息如果验证缓存新鲜，返回304等对应状态码

10. 处理程序读取完整请求并准备HTTP响应，可能需要查询数据库等操作

11. 服务器将响应报文通过TCP连接发送回浏览器

12. 浏览器接收HTTP响应，然后根据情况选择关闭TCP连接或者保留重用，关闭TCP连接的四次握手如下：

    1. 主动方发送Fin=1， Ack=Z， Seq= X报文
    2. 被动方发送ACK=X+1， Seq=Z报文
    3. 被动方发送Fin=1， ACK=X， Seq=Y报文
    4. 主动方发送ACK=Y， Seq=X报文

13. 浏览器检查响应状态吗：是否为1XX，3XX， 4XX， 5XX，这些情况处理与2XX不同

14. 如果资源可缓存，进行缓存

15. 对响应进行解码（例如gzip压缩）

16. 根据资源类型决定如何处理（假设资源为HTML文档）

17. 解析HTML文档，构件DOM树，下载资源，构造CSSOM树，执行js脚本，这些操作没有严格的先后顺序，以下分别解释

18. 构建DOM树：

    1. Tokenizing：根据HTML规范将字符流解析为标记
    2. Lexing：词法分析将标记转换为对象并定义属性和规则
    3. DOM construction：根据HTML标记关系将对象组成DOM树

19. 解析过程中遇到图片、样式表、js文件，启动下载

20. 构建CSSOM树：

    1. Tokenizing：字符流转换为标记流
    2. Node：根据标记创建节点
    3. CSSOM：节点创建CSSOM树

21. 根据DOM树和CSSOM树构建渲染树

    :

    1. 从DOM树的根节点遍历所有可见节点，不可见节点包括：1）`script`,`meta`这样本身不可见的标签。2)被css隐藏的节点，如`display: none`
    2. 对每一个可见节点，找到恰当的CSSOM规则并应用
    3. 发布可视节点的内容和计算样式

22. js解析如下：

    1. 浏览器创建Document对象并解析HTML，将解析到的元素和文本节点添加到文档中，此时document.readystate为loading
    2. HTML解析器遇到没有async和defer的script时，将他们添加到文档中，然后执行行内或外部脚本。这些脚本会同步执行，并且在脚本下载和执行时解析器会暂停。这样就可以用document.write()把文本插入到输入流中。同步脚本经常简单定义函数和注册事件处理程序，他们可以遍历和操作script和他们之前的文档内容
    3. 当解析器遇到设置了async属性的script时，开始下载脚本并继续解析文档。脚本会在它下载完成后尽快执行，但是解析器不会停下来等它下载。异步脚本禁止使用document.write()，它们可以访问自己script和之前的文档元素
    4. 当文档完成解析，document.readState变成interactive
    5. 所有defer脚本会按照在文档出现的顺序执行，延迟脚本能访问完整文档树，禁止使用document.write()
    6. 浏览器在Document对象上触发DOMContentLoaded事件
    7. 此时文档完全解析完成，浏览器可能还在等待如图片等内容加载，等这些内容完成载入并且所有异步脚本完成载入和执行，document.readState变为complete,window触发load事件

23. 显示页面（HTML解析过程中会逐步显示页面）

##### 42.如何进行网站性能优化

、content方面

- 1. 减少HTTP请求：合并文件、CSS精灵、inline Image
  2. 减少DNS查询：DNS查询完成之前浏览器不能从这个主机下载任何任何文件。方法：DNS缓存、将资源分布到恰当数量的主机名，平衡并行下载和DNS查询
  3. 避免重定向：多余的中间访问
  4. 使Ajax可缓存
  5. 非必须组件延迟加载
  6. 未来所需组件预加载
  7. 减少DOM元素数量
  8. 将资源放到不同的域下：浏览器同时从一个域下载资源的数目有限，增加域可以提高并行下载量
  9. 减少iframe数量
  10. 不要404

2、Server方面

- 1. 使用CDN
  2. 添加Expires或者Cache-Control响应头
  3. 对组件使用Gzip压缩
  4. 配置ETag
  5. Flush Buffer Early
  6. Ajax使用GET进行请求
  7. 避免空src的img标签

3、Cookie方面

- 1. 减小cookie大小
  2. 引入资源的域名不要包含cookie

4、css方面

- 1. 将样式表放到页面顶部
  2. 不使用CSS表达式
  3. 使用不使用@import
  4. 不使用IE的Filter

5、Javascript方面

- 1. 将脚本放到页面底部
  2. 将javascript和css从外部引入
  3. 压缩javascript和css
  4. 删除不需要的脚本
  5. 减少DOM访问
  6. 合理设计事件监听器

6、图片方面

- 1. 优化图片：根据实际颜色需要选择色深、压缩
  2. 优化css精灵
  3. 不要在HTML中拉伸图片
  4. 保证favicon.ico小并且可缓存

7、移动方面

- 1. 保证组件小于25k
  2. Pack Components into a Multipart Document

##### 43.语义化的理解

）、为了在没有css代码时，也能呈现很好的内容结构，代码结构，以至于达到没有编程基础的非技术人员，也能看懂一二。（其实，就是为了不穿CSS外衣，裸奔依然好看）。
（2）、提高用户体验，比如：title，alt用于解释名词和图片信息。
（3）、利于SEO，语义化能和搜索引擎建立良好的联系，有利于爬虫抓取更多的有效信息。爬虫依赖于标签来确定上下文和各个关键字的权重。
（4）、方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以语义的方式来渲染网页。
（5）、便于团队开发和维护，语义化更具可读性，如果遵循W3C标准的团队都遵循这个标准，可以减少差异化，利于规范化。

（1）、尽可能少的使用没有语义的div和span元素。
（2）、在对语义要求不明显时，技能使用div也能使用p,那就使用p，以为p默认有上下边距，可以兼容特殊终端。
（2）、不要使用纯样式标签，如：b、font、u等，改用css设置。
（4）、需要强调的文本，可以包含在strong或者em标签中（浏览器预设样式，能用CSS指定就不用他们），strong默认样式是加粗（不要用b，因为没语义），em是斜体（不用i同b）；
（5）、使用表格时，标题要用caption，表头用thead，主体部分用tbody包围，尾部用tfoot包围。表头和一般单元格要区分开，表头标题用th，内容单元格用td；

##### 44.HTML5的离线储存怎么使用，工作原理能不能解释一下？

用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。
原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。

如何使用：
1、页面头部像下面一样加入一个manifest的属性；
2、在cache.manifest文件的编写离线存储的资源；
CACHE MANIFEST
\#v0.11
CACHE:
js/app.js
css/style.css
NETWORK:
resourse/logo.png
FALLBACK:
/ /offline.html
3、在离线状态时，操作window.applicationCache进行需求实现。

##### 45.浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢

在线的情况下，浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。
离线的情况下，浏览器就直接使用离线存储的资源

##### 46.iframe有那些缺点？

1.iframe能够原封不动的把嵌入的网页展现出来。
 2.如果有多个网页引用iframe，那么你只需要修改iframe的内容，就可以实现调用的每一个页面内容的更改，方便快捷。
 3.网页如果为了统一风格，头部和版本都是一样的，就可以写成一个页面，用iframe来嵌套，可以增加代码的可重用。
 4.如果遇到加载缓慢的第三方内容如图标和广告，这些问题可以由iframe来解决。
 **iframe的缺点：**
 1.会产生很多页面，`不容易管理`。
 2.iframe框架结构有时会让人感到迷惑，如果框架个数多的话，可能会出现上下、左右滚动条，会分散访问者的注意力，`用户体验度差`。
 3.代码复杂，无法被一些搜索引擎索引到，这一点很关键，现在的搜索引擎爬虫还不能很好的处理iframe中的内容，所以使用iframe会`不利于搜索引擎优化`。
 4.很多的移动设备（PDA手机）无法完全显示框架，`设备兼容性`差。
 5.iframe框架页面会`增加服务器的http请求`，对于大型网站是不可取的。

##### 48.Doctype作用? 严格模式与混杂模式如何区分？它们有何意义?

  **一、Doctype作用是什么？**

<!DOCTYPE>声明叫做文件类型定义（DTD），声明的作用为了告诉浏览器该文件的类型。让浏览器解析器知道应该用哪个规范来解析文档。<!DOCTYPE>声明必须在 HTML 文档的第一行，这并不是一个 HTML 标签。

**二、严格模式与混杂模式如何区分？它们有何意义？**

**严格模式：**又称标准模式，是指浏览器按照 W3C 标准解析代码。

**混杂模式：**又称怪异模式或兼容模式，是指浏览器用自己的方式解析代码。

**如何区分：**浏览器解析时到底使用严格模式还是混杂模式，与网页中的 DTD 直接相关。

1、如果文档包含严格的 DOCTYPE ，那么它一般以严格模式呈现。**（严格 DTD ——严格模式）** 
2、包含过渡 DTD 和 URI 的 DOCTYPE ，也以严格模式呈现，但有过渡 DTD 而没有 URI （统一资源标识符，就是声明最后的地址）会导致页面以混杂模式呈现。**（有 URI 的过渡 DTD ——严格模式；没有 URI 的过渡 DTD ——混杂模式）** 
3、DOCTYPE 不存在或形式不正确会导致文档以混杂模式呈现。**（DTD不存在或者格式不正确——混杂模式）**
4、HTML5 没有 DTD ，因此也就没有严格模式与混杂模式的区别，HTML5 有相对宽松的语法，实现时，已经尽可能大的实现了向后兼容。**（ HTML5 没有严格和混杂之分）**

**意义：**严格模式与混杂模式存在的意义与其来源密切相关，如果说只存在严格模式，那么许多旧网站必然受到影响，如果只存在混杂模式，那么会回到当时浏览器大战时的混乱，每个浏览器都有自己的解析模式。  

##### 49.HTML全局属性(global attribute)有哪些

参考资料（全局属性兼容性特别不好，几乎各个浏览器很少支持）：

MDN: html global attribute或者W3C HTML global-attributes

accesskey:设置快捷键，提供快速访问元素如aaa在windows下的firefox中按alt + shift + a可激活元素

class:为元素设置类标识，多个类名用空格分开，CSS和javascript可通过class属性获取元素

contenteditable: 指定元素内容是否可编辑

contextmenu: 自定义鼠标右键弹出菜单内容

data-*: 为元素增加自定义属性

dir: 设置元素文本方向

draggable: 设置元素是否可拖拽

dropzone: 设置元素拖放类型： copy, move, link

hidden: 表示一个元素是否与文档。样式上会导致元素不显示，但是不能用这个属性实现样式效果

id: 元素id，文档内唯一

lang: 元素内容的语言

spellcheck: 是否启动拼写和语法检查

style: 行内css样式

tabindex: 设置元素可以获得焦点，通过tab可以导航

title: 元素相关的建议信息

translate: 元素和子孙节点内容是否需要本地化

##### 50.Canvas和SVG有什么区别？

Canvas 和 SVG 都允许您在浏览器中创建图形，但是它们在根本上是不同的

#### SVG

**描述：**

- 一种使用XML描述的2D图形的语言
- SVG基于XML意味着，SVG DOM中的每个元素都是可用的，可以为某个元素附加Javascript事件处理器。
- 在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。

#### 比较

**Canvas**

- 依赖分辨率
- 不支持事件处理器
- 弱的文本渲染能力
- 能够以 .png 或 .jpg 格式保存结果图像
- 最适合图像密集型的游戏，其中的许多对象会被频繁重绘

**SVG**

- 不依赖分辨率
- 支持事件处理器
- 最适合带有大型渲染区域的应用程序（比如谷歌地图）
- 复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）
- 不适合游戏应用

##### 51.如何在页面上实现一个圆形的可点击区域？

##### 52.网页验证码是干嘛的，是为了解决什么安全问题

防止恶意注册和[暴力破解](https://www.baidu.com/s?wd=暴力破解&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao) 所谓恶意注册和[暴力破解](https://www.baidu.com/s?wd=暴力破解&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)都是用软件进行的。 人工注册再快，也需要一项一项输入资料，速度很慢，对服务器基本没有影响。如果没有验证码可以使用软件注册的话，可以同时运行成千上万个线程，一次能注册成千上万个用户，让服务器的数据库很快变得臃肿不堪，运行效率下降。 如果一个无聊的人或竞争对手对某网站怀有敌意，那么这种方法很容易就能让对方瘫痪

##### 53.请描述一下 cookies，sessionStorage 和 localStorage 的区别？

localStorage ———-永久存储，永不失效，除非手动删除 
sessionStorage——–数据存储在窗口对象中，窗口关闭后，数据丢失 
cookies—————–只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭 
作用域： 
sessionStorage不在不同的浏览器窗口共享，即使是同一个页面 
localStorage和cookies是在所有同源窗口中共享的 
适用情况： 
cookies数据始终在同源的http请求中携带（即使不需要），适合保存很小的数据 
sessionStorage和localStorage不会自动的将数据发送给服务器，仅在本地存储

54. ##### CSS选择器有哪些？哪些属性可以继承？

55. 选择符类型	例子	例子描述
    通用选择器	*	
    类别选择器(.class)	.intro	选择class=”intro”的所有元素
    ID选择器(#id)	#first	选择id=”first”的所有元素
    标签选择器(element)	div	选择所有<div>标签
    后代选择器(element element)	div p	选择<div>元素内部的所有<p>元素
    子选择器(element>element)	div>p	选择父元素为<div>的所有<p>元素
    群组选择器(element,element)	div,p	选择所有<div>和<p>元素
    相邻同胞选择器(element+element)	div+p	选择紧接在<div>之后的所有<p>元素
    伪类选择器(:link :visited :active :hover :focus :first-child)	a:link a:visited a:active a:hover input:focus p:first-child	（选择所有未被访问的或所有已被访问的或活动的链接）（选择鼠标指针位于其上链接）（选择获得的焦点的input 元素）
    伪元素选择器(:first-letter :first-line :before :after :lang(language))	p:first-letter p:first-line p:before p:after p:lang(it)	选择每个 元素的首字母；选择每个 元素的首行；在每个 元素的内容之前插入内容；在每个 元素的内容之后插入内容；选择带有以 “it” 开头的 lang 属性值的每个 元素
    属性选择器([attribute] [attribute=value] [attribute~=value] [attribute|=value] )	[target=_blank]	[attribute~=value]选择包含一个以空格分隔的词为value的所有元素；[attribute|=value]选择属性的值等于value，或值以 value- 开头的所有元素
    CSS3新增选择器如下：

    css3新增选择器类型	具体选择器	描述
    层次选择器	p~ul	选择前面有p元素的每个ul元素
    伪类选择器	:first-of-type :last-of-type :only-of-type :only-child :nth-child(n) :nth-last-of-type(n) :last-child :root :empty :target :enabled :disabled :checked :not(selector)	
    属性选择器	[attribute*=value] [attribute^=value] [attribute$=value]	选择属性中包含value值的属性，[attribute~=value] 是指包含value整个单词、选择属性以value开头的所有元素、选择属性以value结束的所有元素
    CSS哪些属性可以继承？ 
    css继承特性主要是指文本方面的继承，盒模型相关的属性基本没有继承特性。 
    不可继承的： 
    display、margin、border、padding、background、height、min-height、max-height、width、min-width、max-width、overflow、position、top、bottom、left、right、z-index、float、clear、 table-layout、vertical-align、page-break-after、page-bread-before和unicode-bidi。 
    所有元素可继承的： 
    visibility和cursor 
    终极块级元素可继承的： 
    text-indent和text-align 
    内联元素可继承的： 
    letter-spacing、word-spacing、white-space、line-height、color、font、font-family、font-size、font-style、font-variant、font-weight、text-decoration、text-transform、direction 
    列表元素可继承的： 

    list-style、list-style-type、list-style-position、list-style-image

56. ##### 55.CSS优先级算法如何计算？

    CSS的specificity特性或非凡性，它是一个衡量css优先级的一个标准，

    既然的标准就有判定规定和计算方式，specificity用一个四位数来表示，

    更像四级从左到右，左的最大级，一级大于一级，数位之间没有进制，

    多个选择符用到同一个元素上时那么specificity上值高的最终获得优先级。

    1、行内样式优先级specificity值为1,0,0,0 高于外部定义

    　　如<div style="height:50px; width:50px;">Div</div>  //行内样式

    　　外部定义指经由<link>或<style>标签定义的规则                                                    

    2、按CSS代码中出现的顺序决定，后者CSS样式居上；（近水楼台 先得月）

    3、!important声明specificity值优先级最高

    4、由继续而得到的样式没有specificity的计算，它低于一切其他规则（比如全局选择符*定义规则）

    ##### 56.CSS3有哪些新特性？

    . CSS3实现圆角（border-radius），阴影（box-shadow），边框图片border-image

    2. 对文字加特效（text-shadow、），强制文本换行（word-wrap），线性渐变（linear-gradient）

    3.旋转,缩放,定位,倾斜：transform:rotate(90deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);

    4. 增加了更多的CSS选择器、多背景、rgba()；

    5. 在CSS3中唯一引入的伪元素是 ::selection ；

    6. 媒体查询(@media)，多栏布局（flex） 

    

    ##### 57.请解释一下CSS3的flexbox（弹性盒布局模型）,以及适用场景？

    Flex是Flexible Box的缩写，意为”弹性布局”，用来为盒状模型提供最大的灵活性。

    任何一个容器都可以指定为Flex布局。

    .box{
    display: flex;
    }
    行内元素也可以使用Flex布局。

    .box{
    display: inline-flex;
    }
    Webkit内核的浏览器，必须加上-webkit前缀。

    .box{
    display: -webkit-flex; / *Safari* /
    display: flex;
    }
    注意，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效。

    二、基本概念
    采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称”项目”。

    容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

    项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

    三、容器的属性
    以下6个属性设置在容器上。

    flex-direction
    flex-wrap
    flex-flow
    justify-content
    align-items
    align-content
    3.1 flex-direction属性
    flex-direction属性决定主轴的方向（即项目的排列方向）。

    .box {
    flex-direction: row | row-reverse | column | column-reverse;
    }

    它可能有4个值。

    row（默认值）：主轴为水平方向，起点在左端。
    row-reverse：主轴为水平方向，起点在右端。
    column：主轴为垂直方向，起点在上沿。
    column-reverse：主轴为垂直方向，起点在下沿。
    3.2 flex-wrap属性
    默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。

    .box{
    flex-wrap: nowrap | wrap | wrap-reverse;
    }
    它可能取三个值。

    （1）nowrap（默认）：不换行。

    （2）wrap：换行，第一行在上方。

    （3）wrap-reverse：换行，第一行在下方。

    3.3 flex-flow
    flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

    .box {
    flex-flow:  || ;
    }
    3.4 justify-content属性
    justify-content属性定义了项目在主轴上的对齐方式。

    .box {
    justify-content: flex-start | flex-end | center | space-between | space-around;
    }

    它可能取5个值，具体对齐方式与轴的方向有关。下面假设主轴为从左到右。

    flex-start（默认值）：左对齐
    flex-end：右对齐
    center： 居中
    space-between：两端对齐，项目之间的间隔都相等。
    space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
    3.5 align-items属性
    align-items属性定义项目在交叉轴上如何对齐。

    .box {
    align-items: flex-start | flex-end | center | baseline | stretch;
    }

    它可能取5个值。具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。

    flex-start：交叉轴的起点对齐。
    flex-end：交叉轴的终点对齐。
    center：交叉轴的中点对齐。
    baseline: 项目的第一行文字的基线对齐。
    stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
    3.6 align-content属性
    align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

    .box {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
    }

    该属性可能取6个值。

    flex-start：与交叉轴的起点对齐。
    flex-end：与交叉轴的终点对齐。
    center：与交叉轴的中点对齐。
    space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
    space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
    stretch（默认值）：轴线占满整个交叉轴。
    四、项目的属性
    以下6个属性设置在项目上。

    order
    flex-grow
    flex-shrink
    flex-basis
    flex
    align-self
    4.1 order属性
    order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

    .item {
    order: ;
    }

    4.2 flex-grow属性
    flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

    .item {
    flex-grow: ; / *default 0* /
    }

    如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

    4.3 flex-shrink属性
    flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

    .item {
    flex-shrink: ; / *default 1* /
    }

    如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。

    负值对该属性无效。

    4.4 flex-basis属性
    flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

    .item {
    flex-basis:  | auto; / *default auto* /
    }
    它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。

    4.5 flex属性
    flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

    .item {
    flex: none | [ <‘flex-grow’> <‘flex-shrink’>? || <‘flex-basis’> ]
    }
    该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。

    建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

    4.6 align-self属性
    align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

    .item {
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
    }

    该属性可能取6个值，除了auto，其他都与align-items属性完全一致。

    ##### 58.用纯CSS创建一个三角形的原理是什么？

    用border  将三个变都设置为空  只留下一一个

    可以用 border-style

    和border-width

    ##### 60.为什么要初始化CSS样式

    1. 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。
    2. 初始化CSS样式主要是提高编码质量，如果不初始化整个页面做完很糟糕，重复的CSS样式很多。去掉标签的默认样式如：margin,padding，其他浏览器默认解析字体大小，字体设置。

    ##### 61.absolute的containing block计算方式跟正常流有什么不同？

    无论属于哪种,都要先找到其祖先元素中最近的 position 值不为 static 的元素,然后再判断：
    1、若此元素为 inline 元素,则 containing block 为能够包含这个元素生成的第一个和最后一个 inline box 的 padding box (除 margin, border 外的区域) 的最小矩形；
    2、否则,则由这个祖先元素的 padding box 构成。如果都找不到,则为 initial containing block。

    补充：
    \1. static(默认的)/relative：简单说就是它的父元素的内容框(即去掉 padding 的部分)
    \2. absolute: 向上找最近的定位为 absolute/relative 的元素
    \3. fixed: 它的 containing block 一律为根元素(html/body),根元素也是 initialcontaining block

    ##### 62.CSS里的visibility属性有个collapse属性值？在不同浏览器下以后什么区别？

    - 在谷歌浏览器里，使用collapse值和使用hidden值没有什么区别。
    - 在火狐浏览器、Opera和IE11里，使用collapse值的效果就如它的字面意思：table的行会消失，它的下面一行会补充它的位置。

    ##### 63.display:none与visibility：hidden的区别？

    一个是直接隐藏

    一个是超出隐藏

    

    64.position跟display、overflow、float这些特性相互叠加后会怎么样？
    65.对BFC规范(块级格式化上下文：block formatting context)的理解？
    66.为什么会出现浮动和什么时候需要清除浮动？清除浮动的方式？
    67.上下margin重合的问题

57. 设置元素浮动后，该元素的display值是多少？
    69.移动端的布局用过媒体查询吗？
    70.CSS优化、提高性能的方法有哪些？
    71.浏览器是怎样解析CSS选择器的？
    72.在网页中的应该使用奇数还是偶数的字体？为什么呢？
    73.margin和padding分别适合什么场景使用？
    74.元素竖向的百分比设定是相对于容器的高度吗？
    75.全屏滚动的原理是什么？用到了CSS的哪些属性？
    76.什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的IE？

58. 视差滚动效果？
    78.::before 和 :after中双冒号和单冒号有什么区别？解释一下这2个伪元素的作用
    79.让页面里的字体变清晰，变细用CSS怎么做？

59. position:fixed;在android下无效怎么处理？
    81.如果需要手动写动画，你认为最小时间间隔是多久，为什么？
    82.li与li之间有看不见的空白间隔是什么原因引起的？有什么解决办法？
    83.display:inline-block 什么时候会显示间隙？

60. 有一个高度自适应的div，里面有两个div，一个高度100px，希望另一个填满剩下的高度
    85.png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过webp？
    86.style标签写在body后与body前有什么区别？
    87.CSS属性overflow属性定义溢出元素内容区的内容会如何处理?
    88.阐述一下CSS Sprites

61. 一行或多行文本超出隐藏