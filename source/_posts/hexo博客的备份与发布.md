---
title: hexo博客的备份与发布
copyright: true
typora-copy-images-to: hexo博客的备份与发布
date: 2019-05-27 17:30:23
tags:
categories:
---





下载hexo模板；

备份hexo博客；

发布hexo博客；

<!--more-->



模板仓库（model_repo）地址：https://github.com/qixiansheng/model_repo.git

主要就是如何使用模板仓库（先下载下来）作为自己仓库的使用教程；

## 基础环境

安装git

安装npm（nodejs）

安装hexo

安装typora

## 具体实施

### 搭建blog本地仓库

1、在github上创建两个远程仓库：

代码备份仓库（如code_repo）

页面发布仓库（如page_repo）

2、 创建本地仓库（code_repo）并测试下是否可以正常提交

```js
git clone   xxx.code_repo.git  
copy model_repo/.  code_repo  //把模板仓库的文件都复制到code_repo里；
git add .   
git commit -m "init blog repo"
git push origin master 
```

3、简单介绍模板仓库的文件作用（可忽略）

```js
_config.yml     //配置文件
package.json      //npm依赖包
package-lock.json  
scaffolds/     
themes/       //主题文件，已经只保留next，hexo默认的lanscape出现过gitpage无法读取它的一个插件无法发布的情况，既然不用它就删掉了
source/  
.gitignore       //哪些文件在git上传时忽略
```

### 安装blog本地环境

我们用的hexo搭建的blog，安装好依赖包并测试是否可正常使用

```js
cd code_repo
npm install  //安装依赖库
hexo g    //生成静态文件
hexo s    //本地启动 查看效果
修改_condfig.yml 配置下page_repo地址  
hexo d  // 发布下试试
```

### hexo的配置文件

```
主要有两处，修改_config.yml：
1、发布地址修改
deploy:
  type: git
  repository:
      repo: https://github.com/qixiansheng/qixiansheng.github.io.git   
  branch: master
  
2、发布的域名是二级目录
root: /xue   一级就/,二级就/xx
```



### hexo使用方法

```
hexo clean
hexo n 'title'   
hexo g  
hexo s
hexo d
```

### git 使用方法

```
git pull
git add .
git commit -m "update info"
git push origin master
```



### 写文章使用typora

```
打开文件夹 直接写就行
文章目录：source\_posts
```



