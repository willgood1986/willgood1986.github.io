---
title: hexo搭建的一些笔记
date: 2020-01-31 08:57:56
tags: 
   - hexo
   - blog
categories: Tech
---

## Node环境准备

1. 这个是通过hexo搭建博客的原始地址[hexo搭建博客](https://blog.annieyu.com/posts/207737771.html)
2. hexo前端是基于node的，windows可以通过[node官网](https://nodejs.org/en/)来安装  node环境
3. 安装**npm**中国版本，可以通过
``` bash
> npm install -g cnpm --registry=https://registry.npm.taobao.org
```

## hexo安装  
1. 安装好node以及包管理器，可以通过命令安装hexo
``` bash
> cnpm install -g hexo
```
2. 在本地的创建一个blog目录，进入hexo目录，并使用hexo初始化
``` bash
> hexo init 
```
3. 安装hexo的依赖包
``` bash
> cnpm install
```
4. 生成静态页面
``` bash
> hexo g
```
5. 启动本地服务 
``` bash
> hexo s
```
6. 其实也可以合并步骤4，5
``` bash
> hexo s -g
```
## 部署到github
1. 在github上面创建一个username.github.io
2. 在本地生成一个SSH key，通过在cmd里面执行ssh-keygen命令,其他的默认即可
``` bash
>ssh-keygen -t rsa -C "username@email.com"
```
3. 在GitHub上面，在个人设置里面，打开Github-settings-SSH and GPG key,将本地的公钥的数据拷贝进去即可
4. 测试密钥,通过以下命令
``` bash
> ssh -T git@github.com
``` 
5. 打开blog根目录下面的__config.yml,修改deploy配置
``` bash
  > type: git
  > repository: git@github.com:username/username.github.io.git
  > branch: master
```
6. 设置git信息
``` bash
> git config --global user.name "username"
> git config --global user.email "username@email.com"
```
7. 安装hexo git部署包
``` bash
> cnpm install hexo-deployer-git --save
```
8. 部署
``` bash
> hexo d -g
```

## 托管
1. 本地git版本控制,进入blog目录
``` bash
> git init
> git add .
> git commit -m "加入初始版本库"
```
2. 添加到远程仓库
``` bash
> git remote add origin git@github.com:username/username.github.io.git
```
3. 创建hexo分支，将源代码添加到hexo分支
``` bash
> git checkout -b hexo
> git push origin hexo 
```
4. 删除本地的master分支(可选)
``` bash
> git branch -d master
```
5. 在本机的工作目录blog克隆远程仓库
``` bash
> git clone git@github.com:username/username.github.io.git ./blog
```
6. 切换到hexo分支
``` bash
> git checkout -b hexo origin/hexo
```
## 创作
1 新建一篇文章
``` bash
> hexo new "article title"
> hexo d -g
> git push origin hexo
```
2 如果文章有更新，可以执行hexo的clean命令
``` bash
> hexo clean 
> hexo d -g
> git push origin hexo 
```
