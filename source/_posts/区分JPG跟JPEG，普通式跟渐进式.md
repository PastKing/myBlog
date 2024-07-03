---
title: 区分JPG跟JPEG，普通式跟渐进式
date: 2024-7-02
tags:
  - - 教程笔记
categories:
  - - 教程笔记
keywords:
  - - JPG
  - - JPEG
description: 这是一个示例文章的描述。
top_img: 'https://img.picgo.net/2024/07/02/AEimg-1718454500-3367acdf2436f8e199.gif'
comments: true
cover: 'https://img.picgo.net/2024/07/02/AEimg-1718454500-3367acdf2436f8e199.gif'
toc: true
toc_number: true
toc_style_simple: false
copyright: true
copyright_author: AE
copyright_info: 本文版权归作者所有。
mathjax: false
katex: false
aplayer: false
highlight_shrink: false
aside: true
swiper_index: 1
top_group_index: 1
background: '#fff'
abbrlink: dcd59c4b
---
## 一、 JPEG介绍
JPEG 是Joint Photographic Experts Group（联合图像专家小组）的缩写，是第一个国际图像压缩标准。JPEG图像压缩算法能够在提供良好的压缩性能的同时，具有比较好的重建质量，被广泛应用于图像、视频处理领域。

### 1.1. JPEG不同场景的解释:
作为委员会：是Joint Photographic Experts Group（联合图像专家小组）的缩写;
作为压缩标准：JPEG是联合图像专家小组制定的图像压缩标准（见1.3）；
作为文件后缀：是采用JPEG压缩标准的图片的一种格式（见1.2）；
1.2. .jpg和.jpeg的区别
这两种扩展名的实质是相同的，我们可以把.jpg的文件改名为.jpeg，而对文件本身不会有任何影响。严格来讲，JPEG的文件扩展名应该为.jpeg，但由于DOS时代的8.3文件名命名原则，PC机使用了.jpg的扩展名，而由于Mac并不限制扩展名的长度，因此当时苹果机上都使用了.jpeg的后缀名。虽然现在windows也可以支持任意长度的扩展名了，但大家已经习惯了.jpg的叫法，因此也就没有强制修正。这种情况类似于.htm和.html的区别。

### 1.3. 四种压缩模式（本文讨论前2种）
基于DCT的连续模式（Sequential DCT-based mode of operation）
即基本JPEG(Baseline JPEG)，一次将图像由左到右、由上到下顺序处理。

基于DCT的渐进模式（Progressive DCT-based mode of operation）
即渐进JPEG(Progressive JPEG)，当图像传输的时间较长时，可将图像分数次处理，以从模糊到清晰的方式来传送图像（效果类似GIF在网络上的传输）。

无失真模式（Lossless mode of operation）
使用预测性编码代替基于DCT的变换，而且在这个模式中没有涉及量化。
分级模式（Hierarchical mode of operation）
图像以数种分辨率来压缩，其目的是为了让具有高分辨率的图像也可以在较低分辨率的设备上显示。
## 二、 基本JPEG和渐进JPEG显示效果
基本JPEG：一次将图像由左到右、由上到下顺序处理。
![](https://img.picgo.net/2024/07/02/AEimg-1718454500-3367acdf2436f8e199.gif)


渐进JPEG：图像分数次处理，以从模糊到清晰的方式来传送图像。
![](https://img.picgo.net/2024/07/02/AEimg-1718454509-17e1a3fafe57962e9b.gif)

## 三、 应用
基本JPEG和渐进JPEG该什么时候使用？

当您的JPEG图像低于10K时，最好保存为基本JPEG（估计有75％的可能性会更小）
对于超过10K的文件，渐进式JPEG将为您提供更好的压缩（在94％的情况下）
Chrome + Firefox + IE9浏览器下，渐进式图片加载更快，而且是快很多，至于其他浏览器，与基本式图片的加载一致，至少不会拖后腿。
渐进式图片也有不足，就是吃CPU吃内存。
## 四、创建渐进JPEG图片
使用Photoshop
文件->导出->存储为Web所用格式->勾选“连续”和“转换为sRGB”->存储