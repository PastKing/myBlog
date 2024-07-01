---
title: 基于Vue、MarkMap、OpenAi开发的思维导图生成器
top_img: https://s21.ax1x.com/2024/07/01/pkcLyrT.png
cover: https://s21.ax1x.com/2024/07/01/pkcLyrT.png
abbrlink: 6794108d
date: 2024-06-05 14:57:51
tags: 
  - ["人工智能"]
  - ["Vue"]
  - ["MarkMap"]
  - ["Ai"]  # 文章标签，用于分类和搜索
categories: 
  - ["人工智能"]
  - ["开源项目"]
keywords: 
  - ["Ai"]
  - ["MarkMap"]  # 文章的关键词，有助于搜索引擎优化（SEO）
description: "这是一个示例文章的描述。"  # 文章的简要描述
comments: true  # 是否允许评论（布尔值，true 或 false）
toc: true  # 是否显示目录（Table of Contents）
toc_number: true  # 目录中是否显示编号
toc_style_simple: false  # 是否使用简单样式的目录
mathjax: false  # 是否启用MathJax用于数学公式显示
katex: false  # 是否启用KaTeX用于数学公式显示
aplayer: false  # 是否启用APlayer音乐播放器
highlight_shrink: false  # 代码高亮时是否缩小
aside: true  # 是否显示侧边栏
swiper_index: 1  # 首页轮播图配置索引，数字越小越靠前
top_group_index: 1  # 首页右侧卡片组配置索引，数字越小越靠前
background: "#fff"  # 背景颜色，必须是16进制颜色且有6位
---


# 项目简介

> 本项目完全开源
> 如果觉得不错麻烦帮忙点一次Star⭐️

本项目是一个结合了Vue、Markmap和OpenAI ChatGPT的思维导图生成工具。用户可以输入标题和内容，通过调用ChatGPT生成思维导图，并支持放大、缩小、适应屏幕和下载功能。

## 效果演示

![](../doc/PastKing_2024-06-05_13-14-09.gif)

### 技术栈
- 前端框架：Vue
- UI组件库：Element Ui
- 思维导图库：Markmap
- 图像生成库：html-to-image
- 文件保存库：file-saver
- AI模型：OpenAI ChatGPT
### 项目结构

```
├── public
│ └── index.html
├── src
│ ├── assets
│ ├── components
│ │ └── MarkdownRenderer.vue
│ ├── views
│ │ └── Home.vue
│ │ └── About.vue
│ ├── App.vue
│ └── main.js
├── .env
├── .gitignore
├── package.json
├── README.md
└── vue.config.js
```

### 下载
源码(GitHub)：[https://github.com/PastKing/MarkMap-OpenAi-ChatGpt](https://github.com/PastKing/MarkMap-OpenAi-ChatGpt) 
源码(Gitee)：[https://gitee.com/past-dust/mindmap-generator](https://gitee.com/past-dust/mindmap-generator)
### 教程

找到项目目录下的.env文件，并修改以下内容：
```
VUE_APP_API_BASE_URL=https://api.openai.com
VUE_APP_API_KEY=your_openai_api_key
```