---
uuid: 100181f1-a670-295e-690c-86972c045d01
title: 本站开源代码
date: 2020-12-09 08:29:36
tags:
  - 其他
toc: true # 是否启用内容索引
sidebar: custom
---
#### [Gitee page](https://gitee.com/) + [Hexo](https://hexo.io/) {theme：pure 和 图片处理插件：hexo-image-link} + [Typory](https://typora.io/)


#### 创建自己仓库，如：

（1）github：
- 自己的项目 https://github.com/xhunmon/
- 新建仓库：https://github.com/xhunmon/xhunmon.github.io
- 生成的自己博客地址：https://xhunmon.github.io

（2）gitee：
- 自己的项目：https://gitee.com/qincji/
- 新建仓库：https://gitee.com/qincji/qincji/
- 生成的自己博客地址：https://qincji.gitee.io

#### 克隆[本项目](https://github.com/xhunmon/pageblog)

> git clone https://github.com/xhunmon/pageblog.git


#### 使用IDE打开项目（如：clion），进行更改

（1）更换根目录的 `_config.yml` 相关：

-  url: http://qincji.gitee.io 改成上面【生成的自己博客地址】

- repo: https://gitee.com/qincji/qincji.git 改成自己创建好能克隆的仓库地址

（2）更换 `themes/pure/_config.yml` 相关：

- 所有关于用户信息替换成自己的。

（3）更换 `themes/pure/languages/zh-CN.yml` 相关：

- 把中文的配置文件所有关于用户信息替换成自己的。

（4）更换 `themes/pure/source` 相关：

- 把图片资源换成自己的。

#### 主题更多使用 

项目中Hexo theme主题来自 [pure](https://github.com/cofess/hexo-theme-pure) ，[更多配置以及API使用请前往官方文档](https://github.com/cofess/hexo-theme-pure/blob/master/README.cn.md) 。

#### [图片处理插件安装](https://cloud.tencent.com/developer/article/1600295)


#### 使用命令

（1）删除自动生成的文件

> hexo clean

（2）生成网页等文件

> hexo g

（3）开启预览服务，浏览器中输入：http://localhost:4000/

> hexo s

（4）更新到github/gitee仓库

> hexo d

（5）如果是gitee仓库必须去当前项目的gitee page页面手动更新


#### nmp代理的两种方式

(1）方式一：安装cnpm镜像代理；安装后使用 cnpm命令代替cpm

> npm install -g cnpm --registry=https://registry.npm.taobao.org


> cnpm install -g @angular/cli

（2）方式二：

> npm config set registry https://registry.npm.taobao.org


#### 其他

- 搭建过程请前往：[我的博客搭建笔记](https://qincji.gitee.io/2020/12/04/other/001blog/notes/)
