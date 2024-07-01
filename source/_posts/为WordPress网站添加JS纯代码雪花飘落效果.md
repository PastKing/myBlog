---
title: 为WordPress网站添加JS纯代码雪花飘落效果
date: '2023-12-25'
tags:
  - - JavaScript
  - - WordPress
categories:
  - - 编程开发
keywords:
  - - JavaScript
  - - 美化
  - - 雪花
  - - WordPress
description: 这是一个示例文章的描述。
top_img: 'https://s21.ax1x.com/2024/07/01/pkcLkgx.jpg'
comments: true
cover: 'https://s21.ax1x.com/2024/07/01/pkcLkgx.jpg'
toc: true
toc_number: true
toc_style_simple: false
mathjax: false
katex: false
aplayer: false
highlight_shrink: false
aside: true
swiper_index: 1
top_group_index: 1
background: '#fff'
abbrlink: 792c6970
---

```JavaScript
<script type="text/javascript">
(function($){
   $.fn.snow = function(options){
   var $flake = $('<div id="snowbox" />').css({'position': 'absolute','z-index':'9999', 'top': '-50px'}).html('❄'),
   documentHeight     = $(document).height(),
   documentWidth  = $(document).width(),
   defaults = {
      minSize   : 10,
      maxSize   : 20,
      newOn     : 1000,
      flakeColor : "#AFDAEF" /* 此处可以定义雪花颜色，若要白色可以改为#FFFFFF */
   },
   options = $.extend({}, defaults, options);
   var interval= setInterval( function(){
   var startPositionLeft = Math.random() * documentWidth - 100,
   startOpacity = 0.5 + Math.random(),
   sizeFlake = options.minSize + Math.random() * options.maxSize,
   endPositionTop = documentHeight - 200,
   endPositionLeft = startPositionLeft - 500 + Math.random() * 500,
   durationFall = documentHeight * 10 + Math.random() * 5000;
   $flake.clone().appendTo('body').css({
      left: startPositionLeft,
      opacity: startOpacity,
      'font-size': sizeFlake,
      color: options.flakeColor
   }).animate({
      top: endPositionTop,
      left: endPositionLeft,
      opacity: 0.2
   },durationFall,'linear',function(){
        $(this).remove()
   });
   }, options.newOn);
    };
    })(jQuery);
$(function(){
    $.fn.snow({
       minSize: 5, /* 定义雪花最小尺寸 */
       maxSize: 50,/* 定义雪花最大尺寸 */
       newOn: 300  /* 定义密集程度，数字越小越密集 */
    });
});
</script>
```