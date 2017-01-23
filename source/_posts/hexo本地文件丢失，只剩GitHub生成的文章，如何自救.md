---
title: hexo本地文件丢失，只剩GitHub生成的文章，如何自救?
date: 2017-1-22 00:14:57
tags: blog
---
# Ha1oS3c

<!--more-->
![](http://ok508kqsu.bkt.clouddn.com/Logo.png?imageView2/2/w/360/h/360/interlace/0/q/100|watermark/2/text/YWxhdWdoaW5n/font/5a6L5L2T/fontsize/500/fill/I0VGRUZFRg==/dissolve/100/gravity/SouthEast/dx/10/dy/10)
# 0x00
为什么博客荒废了辣么久？？主观原因是我懒，客观原因是杂事繁多。
自从七月份的时候手贱一不小心hexo init后，我的markdown文件就丢失了，然后就没更了，趁现在有空，瞎jb折腾了一天一夜，首先肯定是先找回丢失的文件啦，一开始无头绪，然后想了想这不是和电脑重装了的情况雷同么。。于是乎搜到了[使用hexo，如果换了电脑怎么更新博客？](https://www.zhihu.com/question/21193762)
它就说让我github搞个分支，备份我的原始文件，hexo博客框架只是把我写好的markdown解析成html文件然后再随手上传到github里托管。
既然如此，那我也可以先把html文件拿去[在线转换](http://www.atool.org/html2markdown.php)成markdown哈！markdown文件总算找回来了，那剩下的事都是小事啦。

# 0x01
接着搞好hexo下的配置文件_config.yml ,主要改几个地方，在site下修改标题、作者名。

![](http://ok508kqsu.bkt.clouddn.com/site.png)

在Extensions添加rss按钮，修改自己的主题，添加多说评论。

![](http://ok508kqsu.bkt.clouddn.com/ext.png)

在Deployment添加项目地址。hexo版本3.0以上的配置如下：

![](http://ok508kqsu.bkt.clouddn.com/deploy.png)

再配下站点地图(需要安装hexo插件)。 

![](http://ok508kqsu.bkt.clouddn.com/sitemap.png)

这文件算是配好了。

# 0x02
安装插件:

npm install **plugin-name** --save  

rss插件hexo-generator-feed，将上述命令中的『plugin-name』，替换为hexo-generator-feed。

`（e.g. npm install hexo-generator-sitemap --save）`

sitemap的插件是hexo-generator-sitemap

在package.json配置文件里面可以看见你已安装了什么插件。

![](http://ok508kqsu.bkt.clouddn.com/package.png)_

# 0x03
到themes文件里的主题文件(我的是next)的_config.yml，修改favicon网站图标，rss,scheme,avatar头像，百度统计(需要注册)，
duoshuo_shortname(e.g. 注册了fuck.duoshuo.com,那么只填写fuck就行了)，leancloud_visitors。

![](http://ok508kqsu.bkt.clouddn.com/tb.png)

# 0x04 
为了加快图片加载速度，我使用了图床[七牛](https://portal.qiniu.com/signin)，有配送免费空间，对我来说已经足够了。

# 总结
嗯好像该搞的已经搞了，至于其他那些花销功能我没弄，看需求吧，有需要再继续添加，就这样写着博客先，希望能够坚持下去。中途查了好多资料，看得差不多崩溃。但熟悉了git命令和markdown语法，还打造了sublime3来写md文件，也算有些收获，最后提醒各位每次部署完都尽量用git分支做好备份，没事就不要hexo init了。否则博客数量多的时候就只能呵呵了，想救都有心无力哈，时间应该用在刀刃上。

# 参考:
[hexo你的博客](http://ibruce.info/2013/11/22/hexo-your-blog/)
[hexo-git-backup](https://github.com/coneycode/hexo-git-backup)
[介绍Sublime3下两款Markdown插件](http://www.jianshu.com/p/335b7d1be39e)
[hexo本地文件丢失，只剩GitHub生成的文章了](https://segmentfault.com/q/1010000006689534?_ea=1099551)