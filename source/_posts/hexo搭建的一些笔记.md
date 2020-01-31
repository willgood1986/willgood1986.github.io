---
title: hexo搭建的一些笔记
date: 2020-01-31 08:57:56
tags: 后台维护
---

## Node环境准备

1. 这个是通过hexo搭建博客的原始地址[hexo搭建博客](https://blog.annieyu.com/posts/207737771.html)
2. hexo前端是基于node的，windows可以通过[node官网](https://nodejs.org/en/)来安装  node环境
3. 安装**npm**中国版本，可以通过
   > npm install -g cnpm --registry=https://registry.npm.taobao.org

## hexo安装  
1. 安装好node以及包管理器，可以通过命令安装hexo
   > cnpm install -g hexo
2. 在本地的创建一个blog目录，进入hexo目录，并使用hexo初始化
   > hexo init 
3. 安装hexo的依赖包
   > cnpm install
4. 生成静态页面
   > hexo g
5. 启动本地服务 
   > hexo s
6 其实也可以合并步骤4，5
   > hexo s -g

## 部署到git
1. 在github上面创建一个username.github.io
2. 在本地生成一个SSH key，通过在cmd里面执行ssh-keygen命令,其他的默认即可
   >ssh-keygen -t rsa -C "username@email.com"
3. 在GitHub上面，在个人设置里面，打开Github-settings-SSH and GPG key,将本地的公钥的数据拷贝进去即可
4. 测试密钥,通过以下命令
   > ssh -T git@github.com
5. 打开blog根目录下面的__config.yml,修改deploy配置段
   >deploy:
     >type: git
     >repository: git@github.com:username/username.github.io.git
     >branch: master
6 设置git信息
   >git config --global user.name "username"
   >git config --global user.email "username@email.com"
7.安装hexo git部署包
   >cnpm install hexo-deployer-git --save



