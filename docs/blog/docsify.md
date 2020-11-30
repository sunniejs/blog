# docsify搭建高逼格博客

项目地址: [github](https://github.com/sunniejs/blog)    

网站演示:[de](https://sunniejs.github.io/blog/#/)[mo](https://sunniejs.github.io/blog/#/)

![WX20201128-133545@2x.png](https://upload-images.jianshu.io/upload_images/11007391-43470ab3932bcb0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


作为一个有逼格的前端开发，当然要写出一手有逼格的项目文档，让大家看的舒心，用的放心。自从用上docsify，妈妈再也不用担心别人不用我的项目了~

等等等等，那就有请我们今天的主角[docsify](https://docsify.js.org/#/zh-cn/)上场。docsify 是一个动态生成文档网站的工具，当然你也可以用它来写博客，外带设置一张高逼格的封面图，我高冷技术范(sha diao qian duan gou)人设就此诞生。使用Markdown格式写文档，对开发来说简单易上手，一旦入坑无法自拔~

接下来我就一步一步的带大家用docsify建一个blog，废话不多说，直接开干！

## 前期准备

作为一个前端开发，默认你已经会掌握了node npm 等基础技能，以及使用github新建一个项目并且clone到本地。如果以上的基础技能你还不会，就不建议往下看了。建议你直接找花花姐姐手把手教前端入门~

## 快速开始

推荐全局安装 `docsify-cli` 工具，可以方便地创建及在本地预览生成的文档。

```
npm i docsify-cli -g
```

### github新建项目

使用github新建一个项目，并且clone到本地，进入项目根目录，直接通过 `init` 初始化项目。

```
docsify init ./docs
```

使用编辑器打开项目会看到

![WX20201128-125446@2x.png](https://upload-images.jianshu.io/upload_images/11007391-34d45ba472bd98ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 本地预览

```
docsify serve docs
```

执行完命令打开，在浏览器打开 http://localhost:3000/#/ 就可以看到一个非常简单的页面，到这里我们基础已经做好，接下来就是美化她，让她美美哒~
![WX20201128-125709@2x.png](https://upload-images.jianshu.io/upload_images/11007391-db6a7303fa2a4f45.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




## 美化项目

接下来就是美化我们的项目，封面，侧边栏，主题色。打开`docs`目录下的`index.html`找到`window.$docsify`接下来很多进行配置，接下来很多都是在这里面配置的

### 1.设置名字和仓库地址

设置文档名称和仓库地址

```
<!-- index.html -->
<script>
  window.$docsify = {  
     name: 'Sunnie’s Blog', 
     repo: 'https://github.com/sunniejs/blog'
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
```

### 2.设置封面

首先配置 `coverpage`，默认加载的文件为 `_coverpage.md`。具体配置规则见

[配置项#coverpage](https://docsify.js.org/#/zh-cn/cover)

```
  window.$docsify = {  coverpage:true   }
```

新建一个`_coverpage.md`文件，写一些基础的配置，具体的配置说明就直接官网查看吧[cover](https://docsify.js.org/#/zh-cn/cover)

![WX20201128-132351@2x.png](https://upload-images.jianshu.io/upload_images/11007391-df9ef6093341a076.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

还是有点丑呢，快来改改样式吧

[图片上传中...(image-c4cd89-1606632826453-9)]

新建`_media`文件夹新建`custom.css`自定义样式，并且在`index.html`里引入，并引入了一个新字体。

```
 <link rel="stylesheet" href="./_media/custom.css">
 <link href="https://fonts.googleapis.com/css?family=Lobster"rel="stylesheet">
```

![WX20201128-133847@2x.png](https://upload-images.jianshu.io/upload_images/11007391-d10b934fe1b0a359.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

修改下主题色

```
 window.$docsify = {    themeColor: '#25798A' }
```

改了下主题色和字体机上一个好看的封面，一下子就有感觉了

![WX20201128-133545@2x.png](https://upload-images.jianshu.io/upload_images/11007391-f2875e72738fdb17.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 3.配置侧边栏

 显示侧边栏，新建_sidebar.md，配置 `loadSidebar` 选项，具体配置规则见[配置项#loadSidebar](https://docsify.js.org/#/zh-cn/more-pages?id=%e5%ae%9a%e5%88%b6%e4%be%a7%e8%be%b9%e6%a0%8f)。

```
  window.$docsify = {
    loadSidebar:true
  }
```
![WX20201128-193931@2x.png](https://upload-images.jianshu.io/upload_images/11007391-5fbe596713b2c7ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


然后我们就可以看到侧边栏了~

![WX20201128-194125@2x.png](https://upload-images.jianshu.io/upload_images/11007391-5ae3d285285c7743.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 4.写内容

接下来就是写内容了。每一篇文章都是一个`md`文件，直接编辑 `docs/README.md` 就能更新文档内容，然后我们将侧边栏的链接指向该文件即可。为了管理方便新建的其他`md`文件我放到了`blog`文件夹下面。

![WX20201129-133634@2x.png](https://upload-images.jianshu.io/upload_images/11007391-1f9bab930a250e11.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


到此博客的基本内容就结束了。接下来就是如何让别人看到我们的博客。

## 部署

把本地的代码提交到github上(这一步就省略了)。然后我们设置一下，在我们的项目下点击setting 找到GitHub Pages按照下面红框设置，保存好，就可以看到箭头的地址了。

通过这个链接就可以访问到你的文档、博客了。

![WX20201129-143522@2x.png](https://upload-images.jianshu.io/upload_images/11007391-49c6cecbc2c4449b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


最后为了方便访问，我们拿到链接之后再回到code界面，点击设置，将链接填写在描述或者网站一栏，方便大家访问。

![WX20201129-143800@2x.png](https://upload-images.jianshu.io/upload_images/11007391-de83472a2c06ae48.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 总结

[docsify](https://docsify.js.org/#/zh-cn/quickstart)还有很多功能需有待我们探索，今天只是带大家简单的入门，更多内容可以去官网学习。又是努力奋斗的一天，打工人，加油！

## 关于我


 &nbsp;&nbsp;&nbsp;&nbsp;扫描下方二维码:point_down::point_down:关注“前端女塾”

![logo](../_media/640.gif ':size=262x224')

关注公众号：回复“加群”即可加 前端仙女群
