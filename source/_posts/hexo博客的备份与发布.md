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

3、简单介绍模板仓库的文件作用

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
在_condfig.yml 配置下page_repo地址  
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
```



## 配图教程

test_code是示例存储仓库

1、git clone  https://github.com/qixiansheng/test_code.git

2、把下载的模板文件复制到test_code目录下

![1558949853081](../../../code_repo/source/_posts/hexo%E5%8D%9A%E5%AE%A2%E7%9A%84%E5%A4%87%E4%BB%BD%E4%B8%8E%E5%8F%91%E5%B8%83/1558949853081.png)

3、用git提交一下

```
git add .
git commit -m "init-blog"
git push origin master
```

![1558950003867](../../../code_repo/source/_posts/hexo%E5%8D%9A%E5%AE%A2%E7%9A%84%E5%A4%87%E4%BB%BD%E4%B8%8E%E5%8F%91%E5%B8%83/1558950003867.png)

4、安装博客的开发环境

4.1 安装依赖包

```
npm install 
```

![1558950044768](../../../code_repo/source/_posts/hexo%E5%8D%9A%E5%AE%A2%E7%9A%84%E5%A4%87%E4%BB%BD%E4%B8%8E%E5%8F%91%E5%B8%83/1558950044768.png)

4.2 启动测试下博客

```
hexo clean & hexo g & hexo s
```

![1558950190326](../../../code_repo/source/_posts/hexo%E5%8D%9A%E5%AE%A2%E7%9A%84%E5%A4%87%E4%BB%BD%E4%B8%8E%E5%8F%91%E5%B8%83/1558950190326.png)

然后就可以在本地访问下http://127.0.0.1:4000

发布下看看效果

![1558950273569](../../../code_repo/source/_posts/hexo%E5%8D%9A%E5%AE%A2%E7%9A%84%E5%A4%87%E4%BB%BD%E4%B8%8E%E5%8F%91%E5%B8%83/1558950273569.png)

发布成功后访问域名，看看。

![1558950337421](../../../code_repo/source/_posts/hexo%E5%8D%9A%E5%AE%A2%E7%9A%84%E5%A4%87%E4%BB%BD%E4%B8%8E%E5%8F%91%E5%B8%83/1558950337421.png)

5、测试无误了，写个文章发布

5.1 创建文章

```
hexo n "文章"
```

5.2 重复4.2的操作,先本地查看，再发布

```
hexo clean & hexo g 
hexo s
hexo d
```

6、博客备份

写完了也发布出去了，就剩下这个备份了，我们备份到远程git仓库里，还是重复3的操作

```
git add .
git commit -m "back—blog"
git push origin master
```

备份完就完事。记得每次操作前要先 git pull 更新下。

