img here

### 1.2 Staticaly CDN加速

https://cdn.staticaly.com/gh/xxxfhy/pic_bed@main/img

### 1.3 Vercel 部署

此方法加载速度较快，但是需要域名自定义绑定，其优点也是可以绑定自定义域了，目前Vercel每个月限制流量100GB

1. 进入[Vercel控制面板](https://vercel.com/dashboard)新建项目，并`通过Github继续`，选择导入刚刚创建的仓库，然后直接部署即可

   ![img](https://pic.imgdb.cn/item/638b735916f2c2beb1637950.jpg)

   ![img](https://pic.imgdb.cn/item/638b739716f2c2beb16457e3.jpg)

2. 进入该项目控制台后，选择右上角的`View Domains`添加新的域名，添加一个自己域名的二级域名，然后在你对应的域名解析控制台添加对应解析，等待生效。

   ![img](https://pic.imgdb.cn/item/638b749216f2c2beb167070c.jpg)

   ![img](https://pic.imgdb.cn/item/638b745716f2c2beb1665262.jpg)

   ![img](https://pic.imgdb.cn/item/638b74c316f2c2beb1679c5a.jpg)

3. 通过`自定义域名+资源路径`即可访问到对应的资源，例如我这里为`https://picbed.fomal.cc/img/p1.webp`

4. 要更新图片怎么办？只要将资源复制到对应的文件夹，然后再执行一次下面的命令即可：

   ```
   BASH
   # 将更改提交
   git add .
   git commit -m "更新图片"
   # 推送至github仓库
   git push
   ```

   这个命令默认是更新到仓库的`main`分支上，Vercel一旦检测到main分支发送变化就会触发新一轮部署，我们稍候片刻即可通过新的路径访问到新的资源。

### 1.4 Cloudflare 部署

此方法速度比Vercel稍慢，但是可以不需要域名，目前我就在用这个，而且CloudFlare对于普通用户来说几乎不限量了

1. 进入[Cloudflare官网](https://www.cloudflare.com/)注册并登录自己的账号，然后进入控制台后选择左边的`Pages`，再创建一个新项目并通过Git进行连接，所有参数默认直接部署。

2. [
   ![img](https://pic.imgdb.cn/item/638b75f316f2c2beb16a446e.jpg)](https://pic.imgdb.cn/item/638b75f316f2c2beb16a446e.jpg)[![img](https://pic.imgdb.cn/item/638b766b16f2c2beb16ae188.jpg)](https://pic.imgdb.cn/item/638b766b16f2c2beb16ae188.jpg)

3. 通过给出的`初始域名+资源路径`即可访问到的对应资源，例如我这个就是`pic-bed-c6s.pages.dev/img/p1.webp`，当然你也可以绑定自定义域名使用。

   ![img](https://pic.imgdb.cn/item/638b76e116f2c2beb16b7f79.jpg)

   ## 3.PicGo结合Markdown实时上传图片

   - Picgo究竟是什么？这是一个开源软件，开源地址：[Molunerfinn/PicGo](https://github.com/Molunerfinn/PicGo)

   - 引用项目的介绍：这是一个用于快速上传图片并获取图片 URL 链接的工具，关键是他可以与Typora配套一起使用，在粘贴图片的同时上传图片，十分方便！

   - 最新版我这里实测没办法安装一些插件，因此推荐大家安装[v2.3.1-beta.5](https://github.com/Molunerfinn/PicGo/releases/tag/v2.3.1-beta.5)这个版本

     ![img](https://tuchuang.voooe.cn/images/2022/12/30/image.webp)

   - 下载软件后直接一路安装下去就行，建议装在非C盘的任意一个盘。

   ### 3.1 Github图床

   1. 进入软件之后，一路到设置里面取消勾选其他图床，只留下Github图床一项，因为我们的现在要弄Github图床。

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-1.webp)

   2. 然后到Github新建一个仓库，创建仓库的教程前面有讲，这里就不赘述了，`仓库名字`和`描述`随意，最重要的是权限一定要选`public`，这样你的图片才可以随时随地访问到。在图床设置的Github配置处，按照下图填入对应的信息：

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-2.webp)

      自定义域名的格式为：`https://cdn.staticaly.com/gh/用户名/仓库名@main`，比如我的就是`https://cdn.staticaly.com/gh/fomalhaut1998/markdown_pic@main`，对应的`用户名`和`仓库名`记住要换成自己名字，不能有空格！！！

      Token的获取方式为：`右上角头像`->`Setting`->`左边栏Developer Settings`->`左栏Personal access tokens`->`左栏tokens(classic)`

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-3.webp)

      创建Token时，`Note`随意；`Exporation`选`No expiration`，`Select scopes`必须把`repo`这一项勾上，然后点击生成就行

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-4.webp)

      这个时候必须马上复制出现的token，不然后面就看不到了，复制了填进去刚刚的Token选项，随后点击确定保存

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-5.webp)

   3. 随便拖拽一张图片进来上传区域这里，应该就可以上传成功，随后把生成的链接复制就可以，此时打开仓库可以发现图片上传到了指定的文件夹。注意：每个仓库大小限制是1G！！！

   [![img](https://tuchuang.voooe.cn/images/2022/12/30/image-6.webp)](https://tuchuang.voooe.cn/images/2022/12/30/image-6.webp)

   ### 3.2 Vika图床

   Vika图床的服务器在国内，速度是比较快的

   1. 首先在Picgo里面安装Vikadata的插件

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-7.webp)

   2. 我们要填的信息有下面这几项：

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/1672391987585.webp)

   3. 进入[维格表官网](https://vika.cn/)，注册自己的账号并登录，新建一个空白的维格表

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/1672392200825.webp)

   4. 随后点击左下角头像的个人设置，绑定自己的邮箱后，获取`API Token`

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/1672392200835.webp)

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/1672392200842.webp)

   5. 进入刚刚创建的表格后，点击上边的`API`，进入API界面后，依次点击`显示API Token`->`Get 获取`，然后图中框起来的就是我们需要的`维格表ID`和`API Token`

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/1672392201560.webp)

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/1672392249317.webp)

   6. 填进去对应位置后，到上传区域，把图床换成维格表，试试拖拽图片能不能上传！

   ### 3.3 Bilibili图床

   - 由于这个图床用在博客里存在跨域问题，因此不再推荐使用了，开源地址：[typora-plugin-bilibili](https://github.com/xlzy520/typora-plugin-bilibili)
   - 如需了解使用教程，见视频教程[第12期：免费图床综合教程（二）](https://www.bilibili.com/video/BV1ZG411N7LS/)

   ### 3.4 imgtp图床

   - 开源地址：[picgo-plugin-imgtp](https://github.com/Redns/picgo-plugin-imgtp)

   1. 在Picg插件商店搜索并安装该插件

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-8.webp)

   2. 进入[imgtp](https://imgtp.com/)注册并登录自己的账号，记住账号密码，待会儿要用到

   3. 进入控制台，然后进入`设置`，就可以看到右边有`Token`这一项，这些就是我们要的全部信息

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-9.webp)

   4. 随后在imgtp的配置信息里面填上`账号`、`密码`、`Token`这几项即可

      ![img](https://tuchuang.voooe.cn/images/2022/12/30/image-10.webp)

   5. 填进去对应位置后，到上传区域，把图床换成维格表，试试拖拽图片能不能上传！

   

   免费图床综合教程

   https://www.fomal.cc/posts/d7fb1ba1.html

   作者

   Fomalhaut🥝

   发布于

   2022-12-03

   更新于

   2022-12-30

   许可协议

   [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)