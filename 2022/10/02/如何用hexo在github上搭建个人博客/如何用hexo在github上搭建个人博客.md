# 前期准备

## 安装Node.js
[安装地址](https://nodejs.org/en/)
点击16.17.1.LTS
![](./如何用hexo在github上搭建个人博客/1.png)
下载完成后，一直点击下一步进行安装即可
<font color = gree>PS:这个安装包内除了Node.js以外，还包含npm包管理器，这个是等会搭建hexo博客所必须用到的东西。</font>

## 通过npm安装cnpm
接着打开终端,切换到root用户
```
sudo su
```
输入密码
![](./如何用hexo在github上搭建个人博客/2.png)

此时我们可以查看一下刚刚安装的版本
```
node -v
npm -v
```
![](./如何用hexo在github上搭建个人博客/3.png)
此时证明刚刚有成功安装node.js

接着利用npm来安装cmpn，通过镜像圆来解决访问国外网站较慢的问题
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
![](./如何用hexo在github上搭建个人博客/4.png)
![](./如何用hexo在github上搭建个人博客/5.png)

接着用cmpn来安装hexo
```
cnpm install -g hexo-cli
```
![](./如何用hexo在github上搭建个人博客/6.png)

# 通过hexo搭建博客

输入pwd查看当前位置
接着新建一个空白文件夹：
```
mkdir blog
```
PS：后续如果在搭建博客的过程中出现问题的话，可以把该文件夹删掉，再重来接下来的所有步骤
```
cd blog/
```

![](./如何用hexo在github上搭建个人博客/7.png)

接下来可以真正使用hexo来生成我们的博客，先初始化一个博客，输入：
```
sudo hexo init
```

![](./如何用hexo在github上搭建个人博客/8.png)
等待安装初始化完成后，启动我们的博客，输入：
```
hexo s
```
![](./如何用hexo在github上搭建个人博客/9.png)
用浏览器打开http://localhost:4000/
![](./如何用hexo在github上搭建个人博客/10.png)
接着键盘输入control+c断开连接
此时，我们可以创建一篇文章，按照顺序输入以下命令
```
hexo n "第一篇文章"
cd source/_posts/
ls
vim 第一篇文章.md
```
进入vim后可以随便输入点内容,然后保存退出
```
:wq
```
接着按照顺序输入：
```
hexo clean
hexo g
hexo s
```
继续用浏览器打开http://localhost:4000/，就可以看到刚刚写的内容了

## 将博客部署到Github上
接下来，我们先在浏览器上登陆Github，并新建一个仓库
![](./如何用hexo在github上搭建个人博客/11.png)

然后输入Repository name
![](./如何用hexo在github上搭建个人博客/12.png)
Description里面可以简单写一下
![](./如何用hexo在github上搭建个人博客/13.png)
最后点击Creat repository
![](./如何用hexo在github上搭建个人博客/14.png)

接着安装git部署插件，输入：
```
cnpm install --save hexo-deployer-git
```
![](./如何用hexo在github上搭建个人博客/15.png)

然后用vim打开config.yml
```
vim _config.yml
```
到文件最底部，找到# Deployment配置
![](./如何用hexo在github上搭建个人博客/16.png)
在type:后面写上：
![](./如何用hexo在github上搭建个人博客/18.png)
并输入:wq保存退出
PS:repo的地址在这：
![](./如何用hexo在github上搭建个人博客/17.png)

此时将它部署到GitHub上，，先配置git信息，输入
```
git config --global user.name "wujianqiangCode"
git config --global user.email "ijianqiangwu@outlook.com"
```
接着输入：
```
hexo clean
hexo g
hexo d
```
如果出现该报错：
![](./如何用hexo在github上搭建个人博客/19.png)
github在2021年8月14日七夕这天搞事情，如果这天你提交了github代码报错如下：
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
那么就得换成token登陆了，坑爹！

登录自己的github账号，个人设置那里
![](./如何用hexo在github上搭建个人博客/20.png)
![](./如何用hexo在github上搭建个人博客/21.png)
找到Developer seetings，点击进入配置
![](./如何用hexo在github上搭建个人博客/22.png)
最后点击Generate生成令牌
![](./如何用hexo在github上搭建个人博客/23.png)

记得把你的token保存下来，因为你再次刷新网页的时候，你已经没有办法看到它了！！！

之后就可以用自己生成的token登录，把上面生成的token粘贴到输入密码的位置，然后成功hexo d了。

为了方便我们后续不用每次输入密码，我们可以输入：

此时输入https://wujianqiangcode.github.io/就能看到博客了

为了方便不用每次输账号密码，输入：
```
git remote add myrepo  https://github.com/wujianqiangCode
/wujianqiangCode.github.io
git remote set-url myrepo https://<your token>/<your github name>/<your project name>
```
## 更换主题
接着是更换主题，浏览器输入：
```
github.com/litten/hexo-theme-yilia
```
这边推荐可以换成🀄这个作者的主题,将他的主题仓库克隆到我们的themes/yilia文件夹中。
```
git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```
clone完后输入：
```
 vim _config.yml 
 ```
找到theme
![](./如何用hexo在github上搭建个人博客/24.png)
换成yilia后保存退出
![](./如何用hexo在github上搭建个人博客/25.png)

接着输入：
```
hexo clean
hexo g
hexo d
```
此时登陆博客，多刷新几次后就能看到结果
![](./如何用hexo在github上搭建个人博客/26.png)
