---
layout: post
title: "Element UI Upload默认列表闪动问题"
date:   2019-10-08 01:00:20
cover: "/assets/article-logos/element-ui-logo.png"
categories: ElementUI
---

闪动、体验极差，百度貌似都没找到解决办法
## 解决方案如下：
<span>我们先找下原因吧，思考下...</span>
<blockquote>
<p>因为我是用v-for遍历出一个表单，回显的数据（其中包含图片），整个表单绑定的是一个大对象，当我改变这个对象其中的任何一个参数的时候，这个对象都会重新被加载，从而导致了图片闪动的问题！</p>
</blockquote>

<span>最开始，我是直接这样写的，:file-list直接绑定的是遍历出来的item里面的参数</span>
{% highlight ruby %}
<el-form-item
    v-for="(item, i) in editData.clientHomeCarousels"
    :key="item.id"
    :label="item.carousel_title">
    <el-input v-model="item.carousel_title" :id="i"></el-input>
    <el-button type="text" @click="openDialog(item.carousel_title,item.carousel_href,i)">
      <el-icon class="el-icon-paperclip"></el-icon>
    </el-button>
  <el-upload
    action="https://jsonplaceholder.typicode.com/posts/"
    list-type="picture-card"
    :on-preview="handlePictureCardPreview"
    :file-list="fileList[i]"
    :on-remove="handleRemove">
    <i class="el-icon-plus"></i>
  </el-upload>
  <el-dialog :visible.sync="dialogVisible">
    <img width="100%" :src="dialogImageUrl" alt="">
  </el-dialog>
</el-form-item>
{% endhighlight %}

<blockquote>
<p>解决方案是重新创建一个新的对象，用来装默认回显的数据</p>
</blockquote>
<blockquote>
<p>$this.fileList是新创建的一个数组嵌套数组对象</p>
</blockquote>
{% highlight ruby %}
    for (var i = 0; i < _data.clientHomeCarousels.length; i++) {
          $this.fileList.push([{url: _data.clientHomeCarousels[i].carousel_img}])
    }
{% endhighlight %}

<blockquote>
<p>最后:file-list绑定这个对象里面指定的数据就好啦</p>
</blockquote>
{% highlight ruby %}
    :file-list="fileList[i]"
{% endhighlight %}
