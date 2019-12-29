# HTML_question
***

### Q: `doctype`（文档类型）的作用是什么？

A: 在HTML中 `doctype` 有两个主要目的。

-  **对文档进行有效性验证:**
它告诉用户代理和校验器这个文档是按照什么`DTD` 写的。这个动作是被动的，每次页面加载时，浏览器并不会下载`DTD` 并检查合法性，只有当手动校验页面时才启用。
-  **决定浏览器的呈现模式:**
对于实际操作，通知浏览器读取文档时用哪种解析算法。如果没有写，则浏览器则根据自身的规则对代码进行解析，可能会严重影响HTML 排版布局。浏览器有三种方式解析HTML文档。
	* 非怪异（标准）模式
	* 怪异模式
	* 部分怪异（近乎标准）模式

***

### Q: 浏览器标准模式和怪异模式之间的区别是什么？

A: 在“标准模式”(Standards Mode) 页面按照 HTML 与 `CSS `的定义渲染，而在“怪异模式”(Quirks Mode)就是浏览器为了兼容很早之前针对旧版本浏览器设计、并未严格遵循 `W3C `标准的网页而产生的一种页面渲染模式。浏览器基于页面中文件类型描述的存在以决定采用哪种渲染模式；如果存在一个完整的`DOCTYPE`则浏览器将会采用标准模式，而如果它缺失则浏览器将会采用怪异模式

> 浏览器标准模式和怪异模式的区别：
>
> > **盒模型：**
> > 在怪异模式下，盒模型为IE盒模型而非标准模式下的`W3C` 盒模型：在 IE 盒模型中，
> >     box width = content width + padding left + padding right + border left + border right，
> >     box height = content height + padding top + padding bottom + border top + border bottom。
> >     而在 `W3C `标准的盒模型中，box 的大小就是 content 的大小。
> 
> > **图片元素的垂直对齐方式:**
> > 对于`inline`元素和`table-cell`元素，在 IE Standards Mode 下 vertical-align 属性默认> >取值为`baseline`。而当`inline`元素的内容只有图片时，如`table`的单元格`table-> cell`。在 IE Quirks Mode 下，`table`单元格中的图片的 `vertical-align` 属性默认为`bottom`，因此，在图片底部会有几像素的空间。
>
>> **`<table>`元素中的字体:**
>> `CSS `中，描述`font`的属性有`font-family`，`font-size`，`font-style`，`font-weigh`,上述属性都是可以继承的。而在 IE Quirks Mode 下，对于`table` 元素，字体的某些属性将不会从`body`或其他封闭元素继承到`table`中，特别是 `font-size`属性。
>
>> **内联元素的尺寸:**
>> 在 IE Standards Mode 下，non-replaced `inline` 元素无法自定义大小，而在 IE Quirks Mode 下，定义这些元素的`width`和`height` 属性，能够影响该元素显示的大小尺寸。
>
>> **元素的百分比高度:**
>> `CSS `中对于元素的百分比高度规定如下，百分比为元素包含块的高度，不可为负值。如果包含块的高度没有显式给出，该值等同于“auto”（即取决于内容的高度）。所以百分比的高度必须在父元素有声明高度时使用。
>> 当一个元素使用百分比高度时，在 IE Standards Mode 下，高度取决于内容的变化，而在 Quirks Mode 下，百分比高度则被正确应用。
>
>> **元素溢出的处理：**
>
>> 在 IE Standard Mode 下，`overflow`取默认值 `visible`，即溢出可见，这种情况下，溢出内容不会被裁剪，呈现在元素框外。而在 Quirks Mode 下，该溢出被当做扩展`box`来对待，即元素的大小由其内容决定，溢出不会被裁剪，元素框自动调整，包含溢出内容。

***

### Q: 使用 `XHTML `的局限有哪些？

 A: `xhtml `语法要求严格，必须有`head`、`body` 每个`dom `必须要闭合。空标签也必须闭合。例如`<img />`, `<br/>`, `<input />`等。另外要在属性值上使用双引号。一旦遇到错误，立刻停止解析，并显示错误信息。

```te
如果页面使用 'application/xhtml+xml' 会有什么问题吗？
--如果页面使用'application/xhtml+xml',一些老的浏览器会不兼容。
```

***

### Q: 如果网页内容需要支持多语言，你会怎么做？

> 在设计和开发多语言网站时，有哪些问题你必须要考虑？

```text
A: 编码使用`UTF-8`，空间域名需要支持多浏览地址,准备多套模板。
     在设计和开发多语言网站时，需要考虑
     - 应用字符集的选择
     - 语言书写习惯&导航结构
     - 数据库驱动型网站
     - css 盒子会因为内容尺寸不一样出现不对齐偏移
```

***

### Q: `data-`属性的作用是什么？

```html
A: `data-`为前端开发者提供自定义的属性，这些属性集可以通过对象的`dataset`属性获取，不支持该属性的浏览器可以通过`getAttribute`方法获取:

  `<div data-author="david" data-time="2011-06-20" data-comment-num="10">...</div>`

  `div.dataset.commentNum; // 10`

  需要注意的是，`data-`之后的以连字符分割的多个单词组成的属性，获取的时候使用驼峰风格。并不是所有的浏览器都支持.`dataset`属性，测试的浏览器中只有Chrome 和Opera 支持。

  即：当没有合适的属性和元素时，自定义的 data 属性是能够存储页面或 App 的私有的自定义数据。

  > Custom data attributes are intended to store custom data private to the page or application, for which there are no more appropriate attributes or elements.
```

***

### Q:如果把 `HTML5 `看作做一个开放平台，那它的构建模块有哪些？

> A: 开放网络平台:
>
>   > The Open Web Platform is the collection of open (royalty-free) technologies which enables the Web. Using the Open Web Platform, everyone has the right to implement a software component of the Web without requiring any approvals or waiving license fees.
>
>   开放网络平台（Open Web Platform）是一些开放的（免版权）技术的集合，这些技术激活了互联网。使用开放网络平台时，每个人都有权实现 Web 上的一个组件，而不用向任何人索取许可和证书。

```html
  将 HTML5 看做开放网络平台，那它的构建模块有哪些？我想，所谓构建模块，指的应该是开放网络平台这个技术集合中的技术。

  - HTML
  - DOM
  - CSS
  - SVG
  - MathML
  - Web APIs
      + Canvas WebGL
      + Audio
      + Web Storage
      + File, File System
      + History, contentEditable, Drag & Drop, HTML Editing Commands
      + Web Sockets
      + Web Workers
      + Server-Send Events
      + XMLHttpRequest
      + Geolocation, Device Orientation
      + DOM Events, Touch Events, Progress Events
      + Custom application development
      + Clipboard and events
      + Web Notifications, Web Messaging
      + Offine Web Applications
      + Media Capture API
      + Timing control for script-based animations, Page Visibility, Navigation + Timing, Resource Timing
      + Selectors
      + DOM Traversal, DOM XPath, Element Traversal
      + EcmaScript / JavaScript
      + HTTP
      + URI
      + Media Accessibility Checklist

```
```html
语义 - 提供更准确地描述内容。

连接 - 提供新的方式与服务器通信。

离线和存储 - 允许网页在本地存储数据并有效地离线运行。

多媒体 - 在 Open Web 中，视频和音频被视为一等公民（first-class citizens）。

2D/3D 图形和特效 - 提供更多种演示选项。

性能和集成 - 提供更快的访问速度和性能更好的计算机硬件。

设备访问 - 允许使用各种输入、输出设备。

外观 - 可以开发丰富的主题。

作者：iamtianxuan
链接：https://www.jianshu.com/p/2745b6df3b98
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

***

### Q: 请描述一下 cookies，`sessionStorage `和 `localStorage `的区别

###  A: `sessionStorage `和 `localStorage `是`HTML5Web Storage API ` 提供的，可以方便的在web请求之间保存数据。有了本地数据，就可以避免数据在浏览器和服务器间不必要地来回传递。

>  `sessionStorage`、`localStorage`、cookie都是在浏览器端存储的数据，其中`sessionStorage `的概念很特别，引入了一个“浏览器窗口”的概念。`sessionStorage `是在同源的同窗口（或tab）中，始终存在的数据。也就是说只要这个浏览器窗口没有关闭，即使刷新页面或进入同源另一页面，数据仍然存在。关闭窗口后，`sessionStorage `即被销毁。同时“独立”打开的不同窗口，即使是同一页面，`sessionStorage `对象也是不同的

> cookies会发送到服务器端。其余两个不会。

> Microsoft 指出 Internet Explorer 8 增加cookie 限制为每个域名50个，但`IE7 `似乎也允许每个域名50个cookie。Firefox 每个域名cookie 限制为50个。Opera每个域名cookie 限制为30个。Firefox 和Safari 允许cookie 多达4097个字节，包括名（name）、值（value）和等号。Opera 许cookie 多达4096个字节，包括：名（name）、值（value）和等号。Internet Explorer 允许cookie 多达4095个字节，包括：名（name）、值（value）和等号。

    - Cookie
      + 每个域名存储量比较小（各浏览器不同，大致4K）
      + 所有域名的存储量有限制（各浏览器不同，大致4K）
      + 有个数限制（各浏览器不同）
      + 会随请求发送到服务器
    - LocalStorage
      + 永久存储
      + 单个域名存储量比较大（推荐5MB，各浏览器不同）
      + 总体数量无限制
    - SessionStorage
      + 只在 Session 内有效
      + 存储量更大（推荐没有限制，但是实际上各浏览器也不同）
***

### 请描述一下 `GET` 和 `POST` 的区别?

A: 区别如下：
  * get 向指定的资源请求数据,请求的数据会附在URL 之后,就是把数据放置在请求行（request line）中），以?分割URL和传输数据，多个参数用&连接；
  * post 向指定的资源提交要被处理的数据。get 方法，查询请求是在`url`中显示的，有长度限制，get 方法是安全幂等的。而post 方法请求是封装在`http` 消息包体中

| &              | get                | post         |
| -------------- | ------------------ | ------------ |
| 后退/刷新      | 无害               | 请求重新提交 |
| 书签           | 可做书签           | 不可做       |
| 缓存           | 可被缓存           | 不能被缓存   |
| 历史           | 保留在浏览器记录里 | 不保留       |
| 对数据长度限制 | 限制（2048字符）   | 不限制       |
| 安全性         | `url`中暴露数据    | 相对安全     |
| 可见性         | `url`中可见        | 不可见       |

>  - 对于get 来说，是向服务器端请求数据，其请求在`url` 中可见，其长度有限制（2048字符）个体方法是安全幂等，这里的安全是指用于获取信息而非修改信息，幂等是指每次请求得到的结果都一样。
>  - 对于post 来说，是向服务器端提交数据，每次刷新或者后退都会重新提交，post 请求的数据封装在`http` 请求的首部里。

***

### Q: `<keygen>` 是正确的`HTML5`标签吗

A: 是。
`<keygen>` 标签规定用于表单的密钥对生成器字段。当提交表单时，私钥存储在本地，公钥发送到服务器。是`HTML5 `标签。

***

### Q: `<bdo>` 标签是否可以改变文本方向？

A: 可以。
`<bdo>`标签覆盖默认的文本方向。

```html
<bdo dir="rtl">Here is some text</bdo>
```

***

### Q: 下列HTML代码是否正确？

```html
<figure>
    <img src="myimage.jpg" alt="My image">
    <figcaption>
        <p>This is my self portrait.</p>
    </figcaption>
</figure>
```

> A: 正确
>  `<figure>` 标签规定独立的流内容（图像、图表、照片、代码等等）。`figure` 元素的内容应该与主内容相关，但如果被删除，则不应对文档流产生影响。使用`<figcaption>`元素为`figure`添加标题（caption）。

***

### Q: 哪种情况下应该使用`small`标签？当你想在`h1` 标题后创建副标题？还是当在`footer`里面增加版权信息？

A: `small`标签一般使用场景是在版权信息和法律文本里使用，也可以在标题里使用标注附加信息（bootstrap中可见），但不可以用来创建副标题。

```html
The HTML Small Element (<small>) makes the text font size one size smaller (for example, from large to medium, or from small to x-small) down to the browser's minimum font size.  In HTML5, this element is repurposed to represent side-comments and small print, including copyright and legal text, independent of its styled presentation.
```

***

### Q: 在一个结构良好的web网页里，多个`h1`标签会不利于`SEO`吗？

A: 不影响。

```html
According to Matt Cutts (lead of Google's webspam team and the de facto expert on these things), using multiple <h1> tags is fine, as long as you're not abusing it (like sticking your whole page in an <h1> and using CSS to style it back to normal size). That would likely have no effect, and might trigger a penalty, as it looks spammy.
------------------------------------------
If you have multiple headings and it would be natural to use multiple <h1>'s, then go for it.
```

***

### Q: 如果你有一个搜索结果页面，你想高亮搜索的关键词。什么HTML 标签可以使用?

A:`<mark>` 标签表现高亮文本。

​```html
The HTML <mark> Element represents highlighted text, i.e., a run of text marked for reference purpose, due to its relevance in a particular context. For example it can be used in a page showing search results to highlight every instance of the searched for word.
```

***

### Q: 下列代码中`scope` 属性是做什么的？

```css
<article>
    <h1>Hello World</h1>
    <style scoped>
        p {
            color: #FF0;
        }
    </style>
    <p>This is my text</p>
</article>

<article>
    <h1>This is awesome</h1>
    <p>I am some other text</p>
</article>
```

* **A: `scoped` 属性是一个布尔属性。如果使用该属性，则样式仅仅应用到 style 元素的父元素及其子元素。**

***

### `HTML5 `支持块级超链接吗？例如：

```html
<article>
    <a href="#">
        <h1>Hello</h1>
        <p>I am some text</p>
    </a>
</article>
```

A: 支持。

`HTML5`中`<a>` 元素表现为一个超链接，支持任何行内元素和块级元素。

***

### Q: 当下列的HTML代码加载时会触发新的HTTP请求吗？

A: 会哇

```html
<img src="mypic.jpg" style="visibility: hidden" alt="My picture">
```

### Q: 当下列的HTML代码加载时会触发新的HTTP请求吗？

A: 会！

```html
<div style="display: none;">
    <img src="mypic.jpg" alt="My photo">
</div>
```

---

### `main1.css`一定会在`alert('Hello world')`被加载和编译吗?

```html
<head>
    <link href="main1.css" rel="stylesheet">
    <script>
        alert('Hello World');
    </script>
</head>
```

***

### Q: 在`main2.css`获取前`main1`一定必须被下载解析吗？

```html
<!-- No -->
<head>
    <link href="main1.css" rel="stylesheet">
    <link href="main2.css" rel="stylesheet">
</head>
```

### Q: 在`Paragraph 1`加载后`main2.css`才会被加载编译吗？

```html
<!-- Yes -->
<head>
    <link href="main1.css" rel="stylesheet">
</head>
<body>
    <p>Paragraph 1</p>
    <p>Paragraph 2</p>
    <link href="main2.css" rel="stylesheet">
</body>
```

***

 - 浏览器如何渲染，可以查阅如下文章：
    + [浏览器的渲染原理简介](http://coolshell.cn/articles/9666.html)
    + [专题：浏览器:渲染重绘、重排两三事](http://developer.51cto.com/art/201311/418133.htm)
    + [浏览器加载和渲染HTML的顺序以及Gzip的问题](http://www.nowamagic.net/academy/detail/48110160)
    + [从FE的角度上再看输入url后都发生了什么](http://div.io/topic/609)

  - HTML 5 方便的资料可阅读：
    + [你需要知道的五个HTML5新功能](http://www.html5cn.org/article-6180-1.html)
    + [必须知道的七个HTML5新特性](http://camnpr.com/archives/must-know-the-seven-html5-features.html)

***

### HTML 5为什么只需要写 <!DOCTYPE HTML>？

* HTML 5 不基于 `SGML`，因此不需要对`DTD`进行引用，但是需要`doctype`来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；
* 而`HTML4.01`基于`SGML`,所以需要对`DTD`进行引用，才能告知浏览器文档所使用的文档类型。

> **SGML是标准通用标记语言**
>
> HTML是[超文本标记语言](https://link.jianshu.com?t=https://www.baidu.com/s?wd=超文本标记语言&tn=44039180_cpr&fenlei=mv6quAkxTZn0IZRqIHckPjm4nH00T1YdmW0dP1nkuWf4PHNWuHD40ZwV5Hcvrjm3rH6sPfKWUMw85HfYnjn4nH6sgvPsT6KdThsqpZwYTjCEQLGCpyw9Uz4Bmy-bIi4WUvYETgN-TLwGUv3EPH0vP104n16Y)，主要是用于规定怎么显示网页
>
> XML是[可扩展标记语言](https://link.jianshu.com?t=https://www.baidu.com/s?wd=可扩展标记语言&tn=44039180_cpr&fenlei=mv6quAkxTZn0IZRqIHckPjm4nH00T1YdmW0dP1nkuWf4PHNWuHD40ZwV5Hcvrjm3rH6sPfKWUMw85HfYnjn4nH6sgvPsT6KdThsqpZwYTjCEQLGCpyw9Uz4Bmy-bIi4WUvYETgN-TLwGUv3EPH0vP104n16Y)是未来网页语言的发展方向，可能会替代HTML，他和HTML都是由SGML延伸转变而来的，**你可以理解SGML是最早的版本，但现在已经淘汰不用了**
>
> XML和HTML的最大区别就在于 XML的标签是可以自己创建的，数量无限多，而HTML的标签都是固定的而且数量有限。
>
> 还有一个是XHTML也是现在基本上所有网页都在用的标记语言，他其实和HTML没什么本质的区别标签都一样，用法也都一样，**就是比HTML更严格**，比如标签必须都用小写，标签都必须有闭合标签等。

***

## 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

```html
行内元素：a、b、span、img、input、strong、select、label、em、button、textarea
块级元素：div、ul、li、dl、dt、dd、p、h1-h6、blockquote
空元素：即系没有内容的HTML元素，例如：br、meta、hr、link、input、img
```

***

### @import和link引入样式的区别

### 1.从属关系区别

`@import`是 CSS 提供的语法规则，只有导入样式表的作用；`link`是HTML提供的标签，不仅可以加载 CSS 文件，还可以定义 RSS、rel 连接属性等。
### 2.加载顺序区别
加载页面时，link标签引入的 CSS 被同时加载；@import引入的 CSS 将在页面加载完毕后被加载。
### 3.兼容性区别
@import是 CSS2.1 才有的语法，故只可在 IE5+ 才能识别；link标签作为 HTML 元素，不存在兼容性问题。
### 4.DOM可控性区别
可以通过 JS 操作 DOM ，插入link标签来改变样式；由于DOM方法是基于文档的，无法使用@import的方式插入样式。
### 5.权重区别
link引入的样式权重大于@import引入的样式。

***

