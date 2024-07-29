---
title: 「Xposed模块」免Root如何使用Xposed模块进行Hook操作，进而实现去除会员、广告等操作
date: '2024-7-29'
# updated: '2023-10-02'
tags: 
  - ["Android"]
  - ["Xposed"]
  - ["Hook"]
  - ["逆向开发"]  # 文章标签，用于分类和搜索
categories: 
  - ["逆向开发"]
  - ["教程笔记"]  # 文章分类
keywords: 
  - ["Xposed"]
  - ["Hook"]  # 文章的关键词，有助于搜索引擎优化（SEO）
description: 这是一个示例文章的描述。
top_img: https://s21.ax1x.com/2024/07/29/pkqzVKA.png
comments: true
cover: https://s21.ax1x.com/2024/07/29/pkqzVKA.png
toc: true
toc_number: true
toc_style_simple: false
# copyright: false
# copyright_author: 作者名
# copyright_author_href: 'https://author-link.com'
# copyright_url: 'https://article-link.com'
# copyright_info: 本文版权归作者所有。
mathjax: false
katex: false
aplayer: false
highlight_shrink: false
aside: true
swiper_index: 1
top_group_index: 1
background: '#fff'
---
## Xposed模块

## 工具列表
JsHook：https://pan.ltde.cn/s/frrt90
LSPatch：https://pan.ltde.cn/s/8ar6oh
## 教程
本期以`LSPatch`为例，目标软件以`傲软抠图`为例
原则上所有软件通用
### 提取安装包+去签
这步很简单，自行操作
**(带壳的软件不行哦，这步很重要，可以判断这个软件是否可以免Root使用`LSPatch`注入)**
### 修复软件+注入模块
打开`LSPatch`

![](../doc/PastKing_2024-07-29_07-52-58.png)

选择去签的包

![](../doc/PastKing_2024-07-29_07-54-06.png)

选择便携嵌入，并选中我们的Xposed模块

![](../doc/PastKing_2024-07-29_07-54-56.png)

然后点击开始修复
修复成功之后会告诉你修复完之后的apk目录

`Patched files are saved toprimary: MT2/apks`
修复完的包名比较明显
安装修复完的安装包

![](../doc/PastKing_2024-07-29_07-55-46.png)

随后打开软件，就会发现，已经成功

![](../doc/PastKing_2024-07-29_07-58-59.png)
