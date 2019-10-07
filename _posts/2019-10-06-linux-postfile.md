---
layout: post
title: "Linux文件传输"
date:   2019-10-06 11:20:00
cover: "/assets/article-logos/Linux.jpg"
categories: Linux
---
<blockquote><p>上传文件到服务器</p></blockquote>
{% highlight ruby %}
    scp 文件名 root@**.**.***:/home/**/
{% endhighlight %}

<blockquote><p>上传"文件夹"到服务器</p></blockquote>
{% highlight ruby %}
    scp -r 文件名 root@**.**.***:/home/**/
{% endhighlight %}

注：如果是GoogleClould Services 默认是通过密钥连接的，所以要修改配置文件，用户名和密码登录
<blockquote><p>先用密钥登录到服务器</p></blockquote>
{% highlight ruby %}
    ssh -i ~/.ssh/gc_rsa bitnami@34.97.161.142
{% endhighlight %}

<blockquote><p>进入后...</p></blockquote>
{% highlight ruby %}
    #切换到root账号
    sudo -i
{% endhighlight %}

{% highlight ruby %}
    # 设置密码
    passwd
{% endhighlight %}
<blockquote><p>开启SSH权限</p></blockquote>
{% highlight ruby %}
    vi /etc/ssh/sshd_config
{% endhighlight %}

<blockquote><p>找到以下内容并修改</p></blockquote>
{% highlight ruby %}
    PermitRootLogin yes           //默认为no，需要开启root用户访问改为yes
    PasswordAuthentication yes    //默认为no，改为yes开启密码登陆
{% endhighlight %}

<blockquote><p>最后重启</p></blockquote>
{% highlight ruby %}
    reboot
{% endhighlight %}


