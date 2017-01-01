---
title: Hello world!
date: 2016-12-31 21:06:01
tags:
---
参照Hexo[官方文档](https://hexo.io/zh-cn/docs/index.html) 搭建了这个博客，记录下过程。

## 安装Node.js

官方推荐使用[nvm](https://github.com/creationix/nvm) 安装Node.js，由于我使用[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)，安装[zsh-nvm](https://github.com/lukechilds/zsh-nvm) 更加简单。

``` bash
$ git clone https://github.com/lukechilds/zsh-nvm ~/.oh-my-zsh/custom/plugins/zsh-nvm
$ vi ~/.zshrc
$ plugins+=(zsh-nvm)
$ source ~/.zshrc
$ nvm upgrade
$ nvm install stable 
```

## Hexo 配置

``` bash
$ npm install -g hexo-cli --register=https://register.npm.taobao.org # 不用淘宝npm源会出错
$ sudo hexo init ~/workspace/hexo # macOS下需要sudo权限
```

hexo 常用操作

``` bash
$ hexo n # = hexo new 新建一篇文章
$ hexo g # = hexo generate 生成静态文件到plubic目录
$ hexo s # = hexo server 启动服务器，可以访问localhost:4000查看
$ hexo d # = hexo deploy部署到Git
```

## 部署到Github

首先需要在Github上创建仓库 username.github.io，并配置好[SSH key](https://help.github.com/articles/generating-an-ssh-key/)

``` bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
$ pbcopy < ~/.ssh/id_rsa.pub
$ pbcopy < /var/root/.ssh/id_rsa.pub # macOS下需要root权限
```

安装 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)

``` bash
$ npm install hexo-deployer-git --save
```

修改配置文件 _config.yml
``` bash
deploy:
  type: git
  repo: git@github.com:xubao/xubao.github.io.git
  branch: master
```

生成静态文件并发布
``` bash
$ hexo g -d
```


