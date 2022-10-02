## 配置docsify

### 0. 相关链接

- [ GitHub+docsify搭建个人博客_Pwalker的博客-CSDN博客_docsify部署到github上](https://blog.csdn.net/Pwalker/article/details/105434900)
- [docsify+github/gitee搭建个人在线文档_Mark_md的博客-CSDN博客_docsify 代码高亮](https://blog.csdn.net/Mark_md/article/details/121457115)
- [手把手教你用git上传项目到GitHub（图文并茂，这一篇就够了）](https://zhuanlan.zhihu.com/p/193140870)
- [ 上传/更新文件到github_记录踩过的坑只为了更好地填坑-CSDN博客_github 更新](https://blog.csdn.net/u011108439/article/details/80609235)

- [Github——git本地仓库建立与远程连接（最详细清晰版本！附简化步骤与常见错误）_你脸上有BUG的博客-CSDN博客_github本地仓库和远程仓库](https://blog.csdn.net/qq_29493173/article/details/113094143)
- [（已解决）Github pages 报错404无法打开_可可与鱼的博客-CSDN博客_gitee网页显示404怎么解决](https://blog.csdn.net/qq_40157728/article/details/114327987?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2~default~CTRLIST~Rate-1-114327987-blog-108204240.pc_relevant_antiscanv3&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2~default~CTRLIST~Rate-1-114327987-blog-108204240.pc_relevant_antiscanv3&utm_relevant_index=1)
- [【开发工具】解决GitHub Pages制作的个人博客无法访问的问题_恬静的小魔龙的博客-CSDN博客_github pages无法访问](https://blog.csdn.net/q764424567/article/details/108204240)
- [Git报错解决：OpenSSL SSL_read: Connection was reset, errno 10054和Failed to connect to github.com port 443_左手の明天的博客-CSDN博客](https://blog.csdn.net/ywsydwsbn/article/details/118304909)
- git上传详细步骤[git上传及报错error: failed to push some refs to ‘github.com:********.git‘解决 - 代码天地 (codetd.com)](https://www.codetd.com/article/13162039)
- [(1条消息) error: remote origin already exists._前端人，前端魂的博客-CSDN博客](https://blog.csdn.net/weixin_46468143/article/details/115246908)



node.js

[vuepress-theme-reco (newblog-gamma.vercel.app)](https://newblog-gamma.vercel.app/)

[Dashboard – Vercel](https://vercel.com/dashboard)

[Vuepress使用指南(reco) - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/186211549)



[xugaoyi/vuepress-theme-vdoing: 🚀一款简洁高效的VuePress知识管理&博客(blog)主题 (github.com)](https://github.com/xugaoyi/vuepress-theme-vdoing)






### 1. 安装docsify

#### 安装两个软件
- __`Node`__
- __`js`__

#### github账号
- 部署


### 2. 上传到github

#### 2.1 问题

```shell
git push -u origin master
```

- 执行上面语句出现 **error: src refspec master does not match any.** [**解决方法**](https://www.cnblogs.com/Renyi-Fan/p/13833340.html)

- git push错误failed to push some refs to的解决。[**解决方法**](https://blog.csdn.net/rocling/article/details/82956402)

  **执行**

  ```shell
  git pull --rebase origin main
  ```



### 3. 更新

push到云端就可以，要是网站没有更新，那就是代码的问题，找了好久，发现代码有问题，现在总结代码。

##### 创建本地仓库

```shell
git init
git add .
git commit -m "这是注释内容"
git remote add origin https://github.com/xxxx/xxx.git（https://github.com/xxxx/xxx.git就是仓库地址 ）
git push -u origin main


git remote add origin https://github.com/peirsist/peirsist.github.io.git
、
```

##### 更新本地仓库

```shell
git init
git add .
git pull origin main
git push -u origin main
```

### 错误
- [git push后出现错误 ![rejected] master -> master(non-fast-forward](https://www.cnblogs.com/qingheshiguang/p/14777557.html)
	- 执行 git push -f origin master



### 配置Docsify用到的插件

经过以下网站，选择了`themeable-simple`主题，并且安装了插件，才得到现在docsify的模样。

- [Docsify 的 LaTex支持 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/363113255)
- [使用Markmap将docsify中的markdown通过思维导图的形式展示出来 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/352795634)
- [笑脸表情类目所有emoji - 笑脸表情有关的表情符号 - EmojiXD](https://emojixd.com/subgroup/face-smiling)
- [docsify导航栏缩进](https://github.com/iPeng6/docsify-sidebar-collapse)
- [docsify的配置+全插件列表 - 邓邓的流水账 (xhhdd.cc)](https://xhhdd.cc/index.php/archives/80/)
- [Docsify高亮](https://github.com/fzankl/docsify-plugin-flexible-alerts)
- [(ฅ>ω<*ฅ) 噫又好了~Docsify进阶配置 | 小四先生的博客 (zxiaosi.cn)](https://zxiaosi.cn/archives/cd1d42d1.html)
- [主题](https://jhildenbiddle.github.io/docsify-themeable/#/options)
- [font-weight - CSS（层叠样式表） | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-weight)
- [Writing more pages (docsify.js.org)如何写docsify的文件](https://docsify.js.org/#/more-pages?id=sidebar)
- [嵌入PDF](https://github.com/lazypanda10117/docsify-pdf-embed)
- [docsify 构建文档网站之定制功能（全网最全）](https://blog.csdn.net/wugenqiang/article/details/107071378)
-[使用docsify写文档写文档](https://blog.hszofficial.site/recommend/2020/11/18/%E4%BD%BF%E7%94%A8docsify%E5%86%99%E6%96%87%E6%A1%A3/)
- [封面图-视觉中国](https://www1.visualchina.com/creative-image/shu/?assetFormat%5B0%5D=png&page=23)


### 文字高亮示例

```markdown
> [!NOTE]
> An alert of type 'note' using global style 'callout'.
```

> [!NOTE]
> An alert of type 'note' using global style 'callout'.

```markdown
> [!TIP]
> An alert of type 'note' using global style 'callout'.
```
> [!TIP]
> An alert of type 'tip' using global style 'callout'.

```markdown
> [!WARNING]
> An alert of type 'note' using global style 'callout'.
```
> [!WARNING]
> An alert of type 'warning' using global style 'callout'.

```markdown
> [!ATTENTION]
> An alert of type 'note' using global style 'callout'.
```
> [!ATTENTION]
> An alert of type 'attention' using global style 'callout'.

```markdown
> [!TIP|style:callout|label:测试]
> An alert of type 'note' using global style 'callout'.
```
> [!TIP|style:callout|label:测试]
> An alert of type 'tip' using global style 'callout'.

```
?> **Tip** notice with `inline code` and additional placeholder text used to
force the content to wrap and span multiple lines.
```

?> **Tip** notice with `inline code` and additional placeholder text used to
force the content to wrap and span multiple lines.

### docsify的目录结构
2020.4.12

之前的目录结构非常的清楚，但是不太美观，使得看起来非常别扭，不够赏心悦目。于是便换了一种目录结构，是赏心悦目了，但导致结构很麻烦。所有的东西都要放在一个md文件中，例如计算机基础目录下有数据结构、计算机网络分支，整个内容都要在一个md文件中，不够清楚。

于是，利用`[]()`的方式跳转的目标文件，使得原来的文件内容可以不用过长。

下面说明一下：
- 避免一级目录(科研相关、软件安装这些)过于冗长，只在一级目录里放标题，目的来方便查找
- 如果二级目录(数据结构、计算机网络等)需要写大量内容，写单独的md文件，使用`[]()`来定位到二级目录的文件。

保持上面的原则，既可以避免一级目录过于冗长，又可以显得结构清晰。

其实就是之前是在`_sidebar.md`文件中说明了路径，现在是在各个单独的文件说明了路径。

<div align=center>
<img src=img/44.png width = 100%/>
</div>

<div align=center>
<img src=img/45.png width = 100%/>
</div>

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

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


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

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

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
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


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

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

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

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


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


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