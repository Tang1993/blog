#前端面试总结-css篇
>###Journey of a thousand miles begins with a single step.

##1.0 web文档基础

###1.1 对WEB标准以及W3C的理解与认识
1. web标准规范要求，书写标签必须闭合、标签小写、不乱嵌套，可提高搜索机器人对网页内容的搜索几率。--- SEO。结构与表现分离。比如实现圆角，不可以在div里随意的添加很多span，这是影响语义的，可以使用before after等来实现

2. 建议使用外链css和js脚本，从而达到结构与行为、结构与表现的分离，提高页面的渲染速度，能更快地显示页面的内容。
3. 样式与标签的分离，更合理的语义化标签，使内容能被更多的用户所访问、内容能被更广泛的设备所访问、更少的代码和组件， 从而降低维护成本、改版更方便
4. 不需要变动页面内容，便可提供打印版本而不需要复制内容，提高网站易用性

###1.2 xhtml和html有什么区别
HTML是一种基本的WEB网页设计语言，XHTML是一个基于XML的置标语言
最主要的不同：
XHTML 元素必须被正确地嵌套。
XHTML 元素必须被关闭。
标签名必须用小写字母。
XHTML 文档必须拥有根元素

###1.3 Doctype是什么。严格模式与混杂模式-如何触发这两种模式，区分它们有何意义
[w3school链接](http://www.w3school.com.cn/tags/tag_doctype.asp)

<!DOCTYPE> 声明必须是 HTML 文档的第一行，位于 <html> 标签之前。

<!DOCTYPE> 声明不是 HTML 标签；它是指示 web 浏览器关于页面使用哪个 HTML 版本进行编写的指令。

在 HTML 4.01 中，<!DOCTYPE> 声明引用 DTD，因为 HTML 4.01 基于 SGML。DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容。

HTML5 不基于 SGML，所以不需要引用 DTD。

<!DOCTYPE> 声明没有结束标签。

<!DOCTYPE> 声明对大小写不敏感。

**HTML 4.01 Strict**.
该DTD 包含所有 HTML 元素和属性，但**不**包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

**HTML 4.01 Transitional**
该DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

**HTML 4.01 Frameset**
该DTD 等同于 HTML 4.01 Transitional，但允许框架集内容。

	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">

**XHTML 1.0 Strict**
该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。

	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

**XHTML 1.0 Transitional**
该DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。
	
	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

**XHTML 1.0 Frameset**
该DTD 等同于 XHTML 1.0 Transitional，但允许框架集内容。
	
	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">

**XHTML 1.1**
该 DTD 等同于 XHTML 1.0 Strict，但允许添加模型（例如提供对东亚语系的 ruby 支持）。

	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">



标准模式和混杂模式（quirks mode）。在标准模式中，浏览器根据规范呈现页面；在混杂模式中，页面以一种比较宽松的向后兼容的方式显示。混杂模式通常模拟老式浏览器（比如Microsoft IE 4和Netscape Navigator 4）的行为以防止老站点无法工作。

浏览器根据DOCTYPE是否存在以及使用的哪种DTD来选择要使用的呈现方法。如果XHTML文档包含形式完整的DOCTYPE，那么它一般以标准模式呈现。对于HTML 4.01文档，包含严格DTD的DOCTYPE常常导致页面以标准模式呈现。包含过渡DTD和URI的DOCTYPE也导致页面以标准模式呈现，但是有过渡DTD而没有URI会导致页面以混杂模式呈现。DOCTYPE不存在或形式不正确会导致HTML和XHTML文档以混杂模式呈现

##2.0 css样式基础

###2.1 行内元素与块级元素的区别
行内元素与块级元素的区别：行内非替换元素设定width、height无效，宽度可以通过设定padding和margin拉宽，高度可以通过设定line-height定位行内框的高度。

常用行内元素：a img input textarea strong code
常用块级元素：div ul h123456 table form center p

###2.2 <img>标签上title与alt属性的区别是什么？
Alt 当图片不显示时用文字替代
Title 为该属性提供信息

##3.0 兼容问题

###3.1 fixed兼容IE6问题
	/*让position:fixed在IE6下可用! */
 
	.fixed-top /* 头部固定 */{position:fixed;bottom:auto;top:0px;}
	.fixed-bottom /* 底部固定 */{position:fixed;bottom:0px;top:auto;}
	.fixed-left /* 左侧固定 */{position:fixed;right:auto;left:0px;}
	.fixed-right /* 右侧固定 */{position:fixed;right:0px;left:auto;}
	/* 上面的是除了IE6的主流浏览器通用的方法 */
	* html,* html body /* 修正IE6振动bug */{background-image:url(about:blank);background-attachment:fixed;}
	* html .fixed-top /* IE6 头部固定 */{position:absolute;bottom:auto;top:expression(eval(document.documentElement.scrollTop));}
	* html .fixed-right /* IE6 右侧固定 */ {position:absolute;right:auto;left:expression(eval(document.documentElement.scrollLeft+document.documentElement.clientWidth-this.offsetWidth)-(parseInt(this.currentStyle.marginLeft,10)||0)-(parseInt(this.currentStyle.marginRight,10)||0));}
	* html .fixed-bottom /* IE6 底部固定  */{position:absolute;bottom:auto;top:expression(eval(document.documentElement.scrollTop+document.documentElement.clientHeight-this.offsetHeight-(parseInt(this.currentStyle.marginTop,10)||0)-(parseInt(this.currentStyle.marginBottom,10)||0)));}
	* html .fixed-left /* IE6 左侧固定 */{position:absolute;right:auto;left:expression(eval(document.documentElement.scrollLeft));}

众所周知IE6不支持position:fixed，这个bug与IE6的双倍margin和不支持PNG透明等bug一样臭名昭著。前些天我做自己的博客模板的时候，遇到了这个问题。当时就简单的无视了IE6——尽管有几个使用IE6的朋友，一起BS我……但是对于大项目或商业网站，如果有用到这个属性的时候，是不可能直接无视的。
你是如何让position:fixed在IE6中工作的？

本文所使用的技巧是用了一条**Internet Explorer的CSS表达式(expression)**。你不可以直接使用该表达式，因为它可能会因为缓存而不更新。解决这一点的最简单的方式是使用**eval**包裹你的语句。
如何解决“振动”的问题？

显然IE有一个多步的渲染进程。当你滚动或调整你的浏览器大小的时候，它将重置所有内容并重画页面，这个时候它就会重新处理css表达式。这会引起一个丑陋的“振动”bug，在此处固定位置的元素需要调整以跟上你的(页面的)滚动，于是就会“跳动”。
解决此问题的技巧就是使用background-attachment:fixed为body或html元素添加一个background-image。这就会强制页面在重画之前先处理CSS。因为是在重画之前处理CSS，它也就会同样在重画之前首先处理你的CSS表达式。这将让你实现完美的平滑的固定位置元素！
这个方案并不是我提供的。我是在网上的某个地方读到这些的。如果你知道是谁原创了这个方法，请告诉前端观察。
我发现的另外一个小技巧是，你根本无需一个真实的图片！你可以使用一个about:blank替代一个spacer.gif图片，而且它工作的同样出色。

###2. 利用position实现垂直居中
####方法一，利用position
利用绝对定位，让元素的顶部与居中线对齐，再让元素上移 50% 的高度。这个应该不难理解。原理可以用下图来做一个可视化说明：
![position 实现居中](./img/css-0-align-0.png)

	/* 代码实现：
	 * 设定宽度和高度，父节点为 position:relative; CSS是这样写的:
	 */
	.selector {
	     position:absolute;top:50%;。
	     margin-top:-元素自身高度的一半;
	}
####方法二，利用display:table
<table\> 真是各种好用，她是各种布局、居中的法宝。垂直居中对其来说，也是非常简单的事。table cells 的 vertical-align:middle 就可以直接解决。所以实现起也来只要这样一行代码：

	td{ vertical-align:middle; }
####终极解决方法
使用第一方案的问题是，通常我们需要垂直居中的元素高度都是不确实的。这里我们需要用 JS 来实现高度的计算，再实现负边；而第二种方案的局限在于只应用于 <table\>。其实是，我们可能综合这两种方法，来做一个 Hack。

像我们知道的，在 CSS2.1 中，任何元素都可以使用 display:table / display:table-cell来实现与 table 一样的功能。那么，只要支持 display:table 的浏览器，已经可以轻松解决，只要这样写代码：

	<!-- DOM 结构 -->
	<div>
	    <p>content</p>
	</div>
	
	/* CSS 实现 */
	div { display:table; }
	p{ display:table-cell; vertical-align:middle; }

但问题是，这种方法在 IE6/7 是不能实现的，因为他们不支持 display:table 这个特性。那有没有办法不计算高度，利用第一种方案来实现垂直居中呢？其实也未尝不可。看看下面这个 DOM 结构和图示：

	<div class="wrap">
	    <div class="hack">
	        <div class="cnt">
	            content
	        </div>
	    </div>
	</div>

![position 实现居中](./img/css-0-align-0.png)

其实我们只要加多一层。内 .hack 层 top:50%; 再让 .cnt 层相对自身向上提50%。如上图所示。这里有一个 DEMO:

[最终方案DEMO](http://sofish.de/file/demo/align-middle.html "DEMO")

	/* CSS 部分的代码实现：整体代码参见上述 demo*/
	.wrap{
	    width:500px;height:300px;border:3px solid #ddd;margin:0 auto;padding:20px;display:table;
	    *position:relative;
	}
	.hack{
	    display:table-cell;vertical-align:middle;
	    *position:absolute;*top:50%;
	}
	.cnt{
	    *position:relative;*top:-50%;
	}

###3. 行内元素与块级元素的区别
行内元素与块级元素的区别：行内非替换元素设定width、height无效，宽度可以通过设定padding和margin拉宽，高度可以通过设定line-height定位行内框的高度。

常用行内元素：a img input textarea strong code
常用块级元素：div ul h123456 table form center p

###4. 如何居中一个浮动元素
	#wrapper {
	float: left;
	position: relative;
	text-align: left;
	left: 50%;
	}
	#wrapper ul {
	list-style: none;
	position: relative;
	left: -50%;
	}
	#wrapper ul li {
	float: left;
	position: relative; /* For IE6 */
	}
	
	<div id="wrapper">
	<ul>
	<li><a href="#">Button 1</a> </li>
	<li><a href="#">Button 2's a bit longer</a> </li>
	<li><a href="#">Butt 3</a> </li>
	<li><a href="#">Button 4</a> </li>
	</ul>
	</div>

##4.0 常见布局结局方案
> [W3Cplus资源链接](http://www.w3cplus.com/solution/index/)
###5. HTML5中的新特性
拖放
###6. 前端页面有哪三层构成
结构层：主要指DOM节点，HTML/XHTML

样式层：主要是指页面渲染；CSS

脚本层：主要指页面动画效果；JS/AS