---
layout: post
title:  "Jekyll+GitHub Pages搭建个人博客"
date:   2019-08-22 18:23:39
categories: jekyll
---
<h3>环境支持：Ruby(Mac自带Ruby环境，目前Jekyll支持Ruby的版本是2.2.0之后的，否则在后续的安装会报版本不兼容之类的错误)</h3>

<h3>1、安装rvm(Ruby的版本管理工具)</h3>
{% highlight ruby %}
# sudo 不然会报没有权限
  sudo curl -sSL https://get.rvm.io | bash -s stable
{% endhighlight %}

<h3>2、如果Ruby版本比较低，先升级Ruby版本</h3>
{% highlight ruby %}
# 目前我安装的是2.4.0的版本
  rvm install 2.4.0
{% endhighlight %}

<h3>3、安装Gem(Gem是Ruby第三方插件管理器)</h3>
{% highlight ruby %}
# 检查gem版本
  gem -v
# 更新Gem(提示权限)
  gem update --system
{% endhighlight %}
gem update --system。这一步可能需要翻墙，否则会出现404错误。解决办法参考：https://ruby.taobao.org/

<h3>4、安装Jekyll</h3>
{% highlight ruby %}
# 还是以超级权限安装，不然权限错误
  sudo gem install jekyll
# 安装成功之后，查看版本号
  jekyll -v
{% endhighlight %}

<h3 style="padding-top:50px;">把本地环境搭建好之后，我们就需要在GitHub上操作啦,就不上图了，一般人都会咯</h3>
1、创建仓库(注: 一定要选择项目模板类型 ==> Jekyll,否则GitHub Pages打开无法定位到你的index.html);<br>
2、进入你的项目，点击Settings,往下拉 找到GitHub Pages，选上之后选显示<a style="color: green;">https://parkertzh.github.io/myBlog/.</a>;
3、绑定自己的域名，在Setting下面的Custom domain的表单里输入自己的域名；最后在域名控制台解析到GitHub上来，解析类型是指向另外一个域名即可;

然后你可以在[Jekyllthemes官网][jekyll] 下载一些模板

<h3>
<strong>Jekyll的基本使用</strong>
</h3>
1、下载模板以后，cd到目录
{% highlight ruby %}
# 构建jekyll
  jekyll build
# 启动jekyll
  jekyll serve
{% endhighlight %}
2、输入jekyll serve 终端会显示本地的访问地址，一般都是[localhost:4000][base-url],或者你可以修改_config.yml文件里面baseurl的参数
{% highlight ruby %}
baseurl: '/项目名'
{% endhighlight %}



Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
[jekyll-themes]: http://jekyllthemes.org
[base-url]: localhost:4000