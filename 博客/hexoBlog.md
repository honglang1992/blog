---
title: 2018-04-08-hexo构建博客
date:  2018-04-08 12:04:02
categories:
- 个人 
tags:
- 博客
---
# 博客构建
### 采用hexo构建博客
[hexo构建详细说明文档](https://hexo.io/zh-cn/docs/)

**发布新文章流程：**

- 编写markdown语法文件，然后放到source目录下_posts目录
- 执行命令：hexo sever -g
- 如果想部署到 github个人网站 则执行 hexo deploy
- 如果端口已经被占用 则先kill掉上个进程
