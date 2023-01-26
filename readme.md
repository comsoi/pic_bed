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