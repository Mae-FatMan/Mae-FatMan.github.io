---
layout: post
title:  "Markdown——入门指南"
date:   2016-04-12 16:54:34
categories: Markdown
---

* content
{:toc}

* 引用1：文／Te_Lee（简书作者）[原文链接](http://www.jianshu.com/p/1e402922ee32/)
* 引用2：文／xwch（简书作者）[原文链接](http://www.jianshu.com/p/9e5cd946696d)
* 引用3：http://www.ituring.com.cn/article/504
 
### 导语：
> Markdown 是一种轻量级的「标记语言」，它的优点很多，目前也被越来越多的写作爱好者，撰稿者广泛使用。看到这里请不要被「标记」、「语言」所迷惑，Markdown 的语法十分简单。常用的标记符号也不超过十个，这种相对于更为复杂的 HTML 标记语言来说，Markdown 可谓是十分轻量的，学习成本也不需要太多，且一旦熟悉这种语法规则，会有一劳永逸的效果。

---

### 一，使用MarkdownPad(windows, web端使用简书)进行编辑

用户可以通过键盘快捷键和工具栏按钮来使用或者移除 Markdown 格式。MarkdownPad左右栏的分割方式令用户可以实时看到 HTML 格式的 Markdown 文档。

![Alt text](/css/pics/markdowanpad2.png "Markdownpad")

邮箱：Soar360@live.com

授权秘钥：

	GBPduHjWfJU1mZqcPM3BikjYKF6xKhlKIys3i1MU2eJHqWGImDHzWdD6xhMNLGVpbP2M5SN6bnxn2kSE8qHqNY5QaaRxmO3YSMHxlv2EYpjdwLcPwfeTG7kUdnhKE0vVy4RidP6Y2wZ0q74f47fzsZo45JE2hfQBFi2O9Jldjp1mW8HUpTtLA2a5/sQytXJUQl/QKO0jUQY4pa5CCx20sV1ClOTZtAGngSOJtIOFXK599sBr5aIEFyH0K7H4BoNMiiDMnxt1rD8Vb/ikJdhGMMQr0R4B+L3nWU97eaVPTRKfWGDE8/eAgKzpGwrQQoDh+nzX1xoVQ8NAuH+s4UcSeQ==

---

### 二，认识 Markdown

在刚才的导语里提到，Markdown 是一种用来写作的轻量级「标记语言」，它用简洁的语法代替排版，而不像一般我们用的字处理软件 Word 或 Pages 有大量的排版、字体设置。它使我们专心于码字，用「标记」语法，来代替常见的排版格式。例如此文从内容到格式，甚至插图，键盘就可以通通搞定了。目前来看，支持 Markdown 语法的编辑器有很多，包括很多网站（例如简书）也支持了 Markdown 的文字录入。Markdown 从写作到完成，导出格式随心所欲，你可以导出 HTML 格式的文件用来网站发布，也可以十分方便的导出 PDF 格式，这种格式写出的简历更能得到 HR 的好感。甚至可以利用 CloudApp 这种云服务工具直接上传至网页用来分享你的文章，全球最大的轻博客平台 Tumblr，也支持 Mou 这类 Markdown 工具的直接上传。

#### Markdown 官方文档
> 这里可以看到官方的 Markdown 语法规则文档，当然，后文我也会用自己的方式阐述这些语法的具体用法。
>> [创始人 John Gruber 的 Markdown 语法说明](http://daringfireball.net/projects/markdown/syntax)
>> [Markdown 中文版语法说明](http://wowubuntu.com/markdown/)

#### 使用 Markdown 的优点
> * 专注你的文字内容而不是排版样式，安心写作。
> * 轻松的导出 HTML、PDF 和本身的 .md 文件。
> * 纯文本内容，兼容所有的文本编辑器与字处理软件。
> * 随时修改你的文章版本，不必像字处理软件生成若干文件版本导致混乱。
> * 可读、直观、学习成本低。

#### 使用 Markdown 的误区
> We believe that writing is about content, about what you want to say – not about fancy formatting. 
> 我们坚信写作写的是内容，所思所想，而不是花样格式。
> — Ulysses for Mac

+ Markdown 旨在简洁、高效，也由于 Markdown 的易读易写，人们用不同的编程语言实现了多个版本的解析器和生成器，这就导致了目前不同的 Markdown 工具集成了不同的功能（基础功能大致相同），例如流程图与时序图，复杂表格与复杂公式的呈现，虽然功能的丰富并没有什么本质的缺点，但终归有些背离初衷，何况在编写的过程中很费神，不如使用专业的工具撰写来的更有效率，所以如果你需实现复杂功能，专业的图形界面工具会更加方便。当然，如果你对折腾这些不同客户端对 Markdown 的定制所带来高阶功能感到愉悦的话，那也是无可厚非的。
 
![Alt text](/css/pics/markdown2.jpg "Markdown high feature")

---

### 三，Markdown语法

##### Markdown 的目标是实现「易读易写」。

不过最需要强调的便是它的可读性。一份使用 Markdown 格式撰写的文档应该可以直接以纯文本发布，并且看起来不会像是由许多标签或是格式指令所构成。Markdown 语法受到一些既有 text-to-HTML 格式的影响，包括 Setext、atx、Textile、reStructuredText、Grutatext 和 EtText，然而最大灵感来源其实是纯文本的电子邮件格式。

因此 Markdown 的语法全由标点符号所组成，并经过严谨慎选，是为了让它们看起来就像所要表达的意思。像是在文字两旁加上星号，看起来就像*强调*。Markdown 的列表看起来，嗯，就是列表。假如你用过电子邮件，区块引言看起来就真的像是引用一段文字。

##### Markdown 的语法有个主要的目的：用来作为一种网络内容的写作用语言。

Markdown 不是要来取代 HTML，甚至也没有要和它相似，它的语法种类不多，只和 HTML 的一部分有关系，重点不是要创造一种更容易写作 HTML 文档的语法，我认为 HTML 已经很容易写了，Markdown 的重点在于，它能让文档更容易阅读、编写。HTML 是一种发布的格式，Markdown 是一种编写的格式，因此，Markdown 的格式语法只涵盖纯文本可以涵盖的范围。

不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。不需要额外标注这是 HTML 或是 Markdown；只要直接加标签就可以了。

#### 标题

标题是每篇文章都需要也是最常用的格式，在 Markdown 中，如果一段文字被定义为标题，有两种方式：

+ 第一种：通过在文字下方添加“=”和“-”，他们分别表示一级标题和二级标题。
+ 第二种：在文字开头加上 “#”，通过“#”数量表示几级标题。（一共只有1~6级标题，1级标题字体最大）

建议用六级标题，建议在井号后加一个空格，这是最标准的 Markdown 语法。

	# 一级标题
	## 二级标题
	### 三级标题

#### 列表

熟悉 HTML 的同学肯定知道有序列表与无序列表的区别，在 Markdown 下，列表的显示只需要在文字前加上 +  - 或 * 即可变为无序列表，有序列表则直接在文字前加1. 2. 3. 符号要和文字之间加上一个字符的空格。

无序

	* A
	* B
	* C

有序

	1. A
	2. B
	3. C

#### 引用

只需要在文本前加入 > 这种尖括号（大于号）即可

	> 当前阶
	>> 下一阶
	>>> 下下一阶

#### 图片与链接（Links）

插入链接与插入图片的语法很像，区别在一个 !号

	内联图片方式：![](){ImgCap}{/ImgCap "title"}
	引用图片方式：![alt text][id] 
		[id]: /path/to/img.jpg "Title"

	内联链接方式：[example link](http://example.com/).
	引用链接方式：[Google][1] than from [Yahoo][2] or [MSN][3].  
		[1]: http://google.com/        "Google"
		[2]: http://search.yahoo.com/  "Yahoo Search" 
		[3]: http://search.msn.com/    "MSN Search"	
	
#### 粗体与斜体

斜体:将需要设置为斜体的文字两端使用1个“*”或者“_”夹起来
粗体:将需要设置为斜体的文字两端使用2个“*”或者“_”夹起来

	*abcd*
	**abcd**

#### 表格

2种

	| Tables        | Are           | Cool  |
	| ------------- |:-------------:| -----:|
	| col 3 is      | right-aligned | $1600 |
	| col 2 is      | centered      |   $12 |
	| zebra stripes | are neat      |    $1 |

	Book | Car
	233  | 2334

#### 代码框（blockquote）

Markdown下实现也非常简单。我用Tab开头缩进！
实现方式有两种：
第一种：简单文字出现一个代码框。（不是单引号而是左上角的ESC下面~中的）

	` abcd

	`
	abcd efgh
	`

第二种：大片文字需要实现代码框。使用Tab和四个空格。

#### 分割线

分割线的语法只需要 3个*号/3个-号

	***
	---
	-
	----------------

---

### 三，Markdown种使用html语句


只有区块元素──比如 **div** __table__ <pre> <p> 等标签，必需在前后加上空白，以利与内容区隔。而且这些（元素）的开始与结尾标签，不可以用 tab 或是空白来缩排。Markdown 的产生器有智能判断，可以避免在区块标签前后加上没有必要的 <p> 标签。


(This is a regular paragraph.)

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

This is another regular paragraph.
、

http://www.jianshu.com/p/1e402922ee32/
http://www.ituring.com.cn/article/504





---

