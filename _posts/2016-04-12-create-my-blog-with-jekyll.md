---
layout: post
title:  "使用Jekyll开发环境开发，在GitHub上搭建静态博客"
date:   2016-04-12 22:14:54
categories: Jekyll GitHub
---

* content
{:toc}

---
说明：
也是按照如下的一些好博客上一步步搭建的，只是综合一下。为自己所用哈。

参考：
http://www.ezlippi.com/blog/2015/03/github-pages-blog.html
http://www.jianshu.com/p/609e1197754c
http://pizida.com/technology/2016/03/03/use-jekyll-create-blog-on-github/
http://www.tuicool.com/articles/BVVBvu

---
# 相关内容介绍

## GitHub

GitHub 是一个代码托管网站，现在很多开源项目都放在GitHub上。 利用GitHub，可以让全球各地的程序员们一起协作开发。GitHub 提供了一种功能，叫  GitHub Pages , 利用这个功能，我们可以为项目建立网站，当然，这也意味着我们可以通过 GitHub Pages 建立自己的网站。

Github很好的将代码和社区联系在了一起，于是发生了很多有趣的事情，世界也因为他美好了一点点。Github作为现在最流行的代码仓库，已经得到很多大公司和项目的青睐，比如jQuery、Twitter等。为使项目更方便的被人理解，介绍页面少不了，甚至会需要完整的文档站，Github替你想到了这一点，他提供了Github Pages的服务，不仅可以方便的为项目建立介绍站点，也可以用来建立个人博客。

Github Pages有以下几个优点：

* 轻量级的博客系统，没有麻烦的配置
* 使用标记语言，比如Markdown 无需自己搭建服务器
* 根据Github的限制，对应的每个站有300MB空间
* 可以绑定自己的域名

当然他也有缺点：

* 使用Jekyll模板系统，相当于静态页发布，适合博客，文档介绍等。
* 动态程序的部分相当局限，比如没有评论，不过还好我们有解决方案。
* 基于Git，很多东西需要动手，不像Wordpress有强大的后台


## Jekyll

Jekyll是什么？它是一个简单静态博客生成工具，为什么是静态，因为它是不需要数据库的，通过markdown编写静态文件，生成Html页面，它的优点是提升了页面的响应速度，并且让博主可以只专注于写文章，不用再去考虑如何排版（markdown语法很好的解决了排版问题）。

jekyll是一个基于ruby开发的，专用于构建静态网站的程序。它能够将一些动态的组件：模板、liquid代码等构建成静态的页面集合，Github-Page全面引入jekyll作为其构建引擎，这也是学习jekyll的主要动力。同时，除了jekyll引擎本身，它还提供一整套功能，比如web server。我们用jekyll –server启动本地调试就是此项功能。读者可能已经发现，在启动server后，之前我们的项目目录下会多出一个_site目录。jekyll默认将转化的静态页面保存在_site目录下，并以某种方式组织。使用jekyll构建博客是十分适合的，因为其内建的对象就是专门为blog而生的，在后面的逐步介绍中读者会体会到这一点。但是需要强调的是，jekyll并不是博客软件，跟workpress之类的完全两码事，它仅仅是个一次性的模板解析引擎，它不能像动态服务端脚本那样处理请求。

jekyll是如何工作的

在jekyll解析你的网站结构前，需要确保网站目录像下面那样：

	|-- _config.yml
	|-- _includes
	|-- _layouts
	|   |-- default.html
	|   |-- post.html
	|-- _posts
	|   |-- 20011-10-25-open-source-is-good.html
	|   |-- 20011-04-26-hello-world.html
	|-- _site
	|-- index.html
	|-- images
	   |-- css
	       |-- style.css
	   |-- javascripts

* _config.yml：保存配置，该配置将影响jekyll构造网站的各种行为。

* _includes：该目录下的文件可以用来作为公共的内容被其他文章引用，就跟C语言include头文件的机制完全一样，jekyll在解析时会对{ % include file.ext %}标记扩展成对应的在_includes文件夹中的文件

* _layouts：该目录下的文件作为主要的模板文件

* _posts：文章或网页应当放在这个目录中，但需要注意的是，文章的文件名必须是YYYY-MM-DD-title

* _site：上面提到过，这是jekyll默认的转化结果存放的目录

* images：这个目录没有强制的要求，主要目的是存放你的资源文件，图片、样式表、脚本等。

---

# Jekyll搭建过程

可以去jekyll官网 [http://jekyllrb.com/](http://jekyllrb.com/)查看说明。

## 安装Ruby

jekyll本身基于Ruby开发，因此，想要在本地构建一个测试环境需要具有Ruby的开发和运行环境。，下载rubyinstaller-2.3.0-x64.exe并安装，配置环境变量。

在命令提示符中，得到ruby版本号，如，即安装成功

	ruby -v

下载地址：[https://www.ruby-lang.org/en/downloads/](https://www.ruby-lang.org/en/downloads/)

## 安装DevKit

下载DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe并安装，配置环境变量。

下载下来的是一个很有意思的sfx文件，可以直接双击，它会自解压到你所选择的目录。解压完成之后，用cmd进入到刚才解压的目录下，运行下面命令，该命令会生成config.yml。（这种安装方式让我想起了，linux下安装三步走config->make->make install中的config）

	$ruby dk.rb init

config.yml文件实际上是检测系统安装的ruby的位置并记录在这个文件中，以便稍后使用。但上面的命令只针对使用rubyinstall安装的ruby有效，如果是其他方式安装的话，需要手动修改config.yml。我生成的config.yml文件内容如下：（加入Ruby路径 C:/Android/Ruby23-x64）

	# This configuration file contains the absolute path locations of all
	# installed Rubies to be enhanced to work with the DevKit. This config
	# file is generated by the 'ruby dk.rb init' step and may be modified
	# before running the 'ruby dk.rb install' step. To include any installed
	# Rubies that were not automagically discovered, simply add a line below
	# the triple hyphens with the absolute path to the Ruby root directory.
	#
	# Example:
	#
	# ---
	# - C:/ruby19trunk
	# - C:/ruby192dev
	#
	---
	- C:/Android/Ruby23-x64

最后，执行如下命令，执行安装：

	$ruby setup.rb

$ruby setup.rb

	$ruby dk.rb install

下载地址：[DevKit](http://rubyinstaller.org/downloads/)

## 安装RubyGems

Rubygems是类似Radhat的RPM、centOS的Yum、Ubuntu的apt-get的应用程序打包部署解决方案。Rubygems本身基于Ruby开发，在Ruby命令行中执行。我们需要它主要是因为jekyll的执行需要依赖很多Ruby应用程序，如果一个个手动安装比较繁琐。jekyll作为一个Ruby的应用，也实现了Rubygems打包标准。只要通过简单的命令就可以自动下载其依赖。

**新版的Ruby自带gem了，gem安装跳过。**

下载解压后，用cmd进入到解压后的目录，执行命令即可：

	$ruby setup.rb

下载地址：[http://rubygems.org/pages/download](http://rubygems.org/pages/download) 

## 用RubyGems安装Jekyll

有了上面的基础，安装jekyll就十分轻松了，在此之前，建议国内用户换成淘宝服务器，速度更快：

	$ sudo gem sources --remove http://rubygems.org/
	$ sudo gem sources -a http://ruby.taobao.org/
执行下面gem命令即可全自动搞定：

	$gem install jekyll
jekyll依赖的组件如下：

	- directory_watcher
	- liquid
	- open4
	- maruku
	- classifier
	

## 测试jekyll服务

安装好之后就可以测试我们的环境了。用cmd进入到上一节我们创建的目录，执行下面命令：

	$jekyll --server --safe

jekyll此时会在localhost的4000端口监听http请求，用浏览器访问http://localhost:4000/index.html，之前的页面出现了！

## 安装nodejs及其配置环境


---

### 创建博客

在d盘新建一个工作区jekyllWorkspace

cd到jekyllWorkspace   

执行jekyll new name创建新的工作区   

![jekyllWorkSpace]({{"/css/pics/jekyllWorkSpace.png"}})   

文件结构如下：   

![jekyllFiles]({{"/css/pics/jekyllFiles.png"}})

cd到博客文件夹，开启服务器   

![serve]({{"/css/pics/serve.png"}})   

watch为了检测文件夹内的变化，即修改后不需要重新启动jekyll

我的环境下启动报错(你的可能没有)，再安装yajl-ruby和rouge  

![yajl]({{"/css/pics/yajl.png"}})

再次启动服务器成功

![serve-sucess]({{"/css/pics/serve-sucess.png"}})

访问 http://localhost:4000/   

![browser]({{"/css/pics/browser.png"}})   

详细文章页面   

![browser2]({{"/css/pics/browser2.png"}})  

---

##后续 

*  整个安装过程参考了jekyll官网，注意jekyll还有一个简体中文官网，不过比较坑（我就被坑了），有些内容没有翻译过来，有可能会走弯路，建议如果想看中文的相关资料，也要中英对照着阅读。[jekyll中文网 http://jekyllcn.com](http://jekyllcn.com), [jekyll英文网 http://jekyllrb.com](http://jekyllrb.com)
*  jekyll中的css是用sass写的，当然直接在`_sass/_layout.scss`中添加css也是可以的。
*  本文是用Markdown格式来写的，相关语法可参考： [Markdown 语法说明 (简体中文版) http://wowubuntu.com/markdown/](http://wowubuntu.com/markdown/)  
*  按照本文的说明搭建完博客后，用`github Pages`托管就可以看到了。注意，在github上面好像不支持rouge，所以要push到github上时，我将配置文件_config.yml中的代码高亮改变为`highlighter: pygments`就可以了
*  博客默认是没有评论系统的，本文的评论系统使用了多说，详细安装办法可访问[多说官网 http://duoshuo.com/](http://duoshuo.com/)，当然也可以使用[搜狐畅言 http://changyan.sohu.com/](http://changyan.sohu.com/)作为评论系统。	
*  也可以绑定自己的域名，如果没有域名，可以在[godaddy http://www.godaddy.com/](http://www.godaddy.com/)上将域名放入购物车等待降价，买之。
*  祝各位新年快乐！

---

## 可能出现的问题

### `hitimes/hitimes (LoadError)`

**错误代码：**

<pre><code class="markdown">C:/Ruby22/lib/ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require': cannot load such file -- hitimes/hitimes (LoadError)</code></pre>

**解决方法：**

在stackoverflow上又一个很好的解决方法。[hitimes require error when running jekyll serve on windows 8.1](http://stackoverflow.com/questions/28985481/hitimes-require-error-when-running-jekyll-serve-on-windows-8-1) 虽然上面的题主问的是 win 8.1 系统下的情况，但是同样适用于 win7。下面我简单翻译一下错误原因和解决方法。

> 可能是 Ruby 2.2 和 hitimes-1.2.2-x86-mingw32 中有一些 ABI 变化，少了一些相关的类库。
> 
> 所以卸载 hitimes 并通过 `--platform ruby` 重装即可。代码如下：
>
><pre><code class="markdown">gem uni hitimes
**Remove ALL versions**
gem ins hitimes -v 1.2.1 --platform ruby
</code></pre>
> 然后将自动重新编译 hitimes 并适用于 Ruby 2.2

下面是我自己的卸载和安装过程：

<pre><code class="markdown">E:\GitWorkSpace\gaohaoyang.github.io>gem uni hitimes

You have requested to uninstall the gem:
        hitimes-1.2.2-x86-mingw32

timers-4.0.1 depends on hitimes (>= 0)
If you remove this gem, these dependencies will not be met.
Continue with Uninstall? [yN]  y
Successfully uninstalled hitimes-1.2.2-x86-mingw32

E:\GitWorkSpace\gaohaoyang.github.io>gem ins hitimes -v 1.2.1 --platform ruby
Fetching: hitimes-1.2.1.gem (100%)
Temporarily enhancing PATH to include DevKit...
Building native extensions.  This could take a while...
Successfully installed hitimes-1.2.1
Parsing documentation for hitimes-1.2.1
Installing ri documentation for hitimes-1.2.1
Done installing documentation for hitimes after 1 seconds
1 gem installed</code></pre>


关于，[hitimes](https://rubygems.org/gems/hitimes/versions/1.2.2) 是一个快速的高效的定时器解决方案库，详情可以去官网查看。


