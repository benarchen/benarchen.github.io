---
title: Github + hexo 搭建个人 Blog
data: 2018-04-07
---

## Github + hexo 搭建个人 Blog

### 整体流程：

1. 安装 node.js 环境
2. 搭建 git 环境
3. Github 账号注册及仓库创建
4. 安装配置 Hexo
5. 关联本地 Hexo 与Github Pages
6. 个人域名解析
7. 未完待续

### 安装 node.js

安装 node 的原因？ --因为 Hexo 博客系统是基于 Node.js 编写的 。

在 Node.js 官网：<https://nodejs.org/en/> 下载安装包 

保持默认设置即可，一路Next，安装很快就结束了。

然后打开命令提示符，输入 `node -v`、`npm -v`，出现版本号则说明 Node.js 环境配置成功，第一步完成！！！

![img](https://github.com/benarchen/picture/blob/master/2018-04-03_014800.png?raw=true)



### 搭建 Git 环境

为什么要搭建 Git 环境？ - 因为需要把本地的网页和文章等提交到 GitHub 上。

Git 是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。在 Git 官网：<https://git-scm.com/>  下载安装包安装。

鼠标在桌面右键出现 Git GUI Here 和 Git Bash Here 及输入 git --version则表示 git 安装成功！

![img](https://github.com/benarchen/picture/blob/master/2018-04-05_104554.png?raw=true)



### Github 账号注册及仓库建立

GitHub 是一个代码托管平台，因为只支持 Git 作为唯一的版本库格式进行托管，故名 GitHub。

Github注册：<https://github.com/>

注册好账号登录进去可以进行相关的设置，接着是创建仓库，这里创建的仓库就是你以后存放博客的地方，所以这里的仓库名必须你的 Github 用户名，比如我的就是 benarchen ，那么我的博客在 Github 上的二级域名就是 https://benarchen.github.io/  当然你以后可以自己域名解析。

![2018-04-05_104555](https://github.com/benarchen/picture/blob/master/2018-04-05_104555.png?raw=true)

填写仓库名，我这里显示已经存在了，因为我之前就创建好了

![2018-04-06_233918](https://github.com/benarchen/picture/blob/master/2018-04-05_105638.png?raw=true)

到此为止仓库就建好了。



### 安装配置 hexo

Hexo 是一个快速、简洁且高效的博客框架，使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

在命令行中输入：

```
npm install hexo-cli -g
```

如果没有反应暂时等一会。

安装完成后检查版本验证是否安装成功

```
hexo --version
```

![2018-04-05_110108](https://github.com/benarchen/picture/blob/master/2018-04-05_110108.png?raw=true)

安装 Hexo 完成后，请执行下列命令来初始化 Hexo，用户名改成你的，Hexo 将会在指定文件夹中新建所需要的文件。

```
hexo init benarchen.github.io

cd benarchen.github.io

npm install
```

这样就在本地电脑创建了一个 blog 文件（仓库），文件路径取决于你的命令行现在处于什么路径。我的是在当前的 Desktop 。

创建好了就应该 run 起来玩玩了，这时我们可以使用命令 hexo server 或者 hexo s  命令将 hexo 服务 run 起来，但是你会遇到一个问题：当你在命令行输入  hexo server 或者 hexo s  命令时系统会提示你找不到该命令。

解决：这时因为在 hexo 3.0 版本之后 server 被单独出来了，我们需要单独安装 server ，安装命令如下：

```
npm install hexo-server
```

安装好 server 之后再进行上面的步骤![2018-04-05_112043](https://github.com/benarchen/picture/blob/master/2018-04-05_112043.png?raw=true)

这时你再访问本机的 4000 端口就会发现 hexo 已经在本机 run 起来了！![2018-04-05_112013](https://github.com/benarchen/picture/blob/master/2018-04-05_112013.png?raw=true)

是不是很激动，还早呢，现在只有你自己能看到，下面我们还需要让别人（全世界）都能看到！



### 关联 Hexo 与 GitHub Pages

我们需要全世界看到我们的 Blog ，就需要把我们的 本地 Hexo 与Github Pages关联，那么如何让他们联系起来呢？ 用 SSH keys

**第一步**：生成 SSH keys，在本地 Git 仓库输入以下命令

```
ssh-keygen -t rsa -C "benarchen.yun@gmail.com"
```

在回车中会提示你输入一个密码，这个密码会在你提交项目时使用，如果为空的话提交项目时则不用输入，我们按回车不设置密码。

**第二步**：添加 SSH key 到 Github（意思就是把你这台电脑和你的 Github 账号绑定，因为 key 中包含了你本机的 MAC 地址）

在上面的命令过后，找到 id_rsa.pub 文件，这个文件的位置在你生成 SSH key 后在命令行中会有，自己仔细看一下命令提示，用记事本打开这个文件，复制全部内容粘贴到你 Github 账号的 setting 选项中的 ssh下添加的new SSH key 中。

**第三步**：测试 SSH key 是否绑定成功

```
ssh -T git@github.com		*注意，这里的 git@github.com 部分不用修改，直接复制也可。
```

![2018-04-06_145654](https://github.com/benarchen/picture/blob/master/2018-04-06_145654.png?raw=true)



如图所示即为成功，如果出现不同的命令提示，应该是询问 yes or no 的，输入 yes 回车即可。



**第四步**：配置 Git 个人信息

现在你已经可以通过 SSH 链接到 GitHub 了，但还有一些个人信息需要完善。Git 会根据用户的名字和邮箱来记录提交。GitHub 也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的就可以了。

```
git config --global user.name "benarchen"
git config --global user.email "benarchen.yun@gmail.com"
```

**第五步**：Deployment

在自己本地的 Git 仓库中找到 _config.yml  文件，用记事本或其它文本编辑器打开，找到 Deployment 然后作以下修改：

```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: git@github.com:benarchen/benarchen.github.io.git
  branch: master
```

第六步：本地文件提交到 Github pages

```
// 删除旧的 public 文件
hexo clean

// 生成新的 public 文件
hexo generate
或者
hexo g

// 开始部署
hexo deploye
或者
hexo d
```

在浏览器中访问 http://benarchen.github.io (注意改成你自己的用户名)，如果出错了，那大概率是因为缺少一个扩展，用下面的命令安装：

```
npm install hexo-deployer-git --save
```

安装好重新进行上面步骤，至此，你就成功的把自己的 Blog 托管到 Github 上了，现在全世界都能看到你了！



### 个人域名解析

