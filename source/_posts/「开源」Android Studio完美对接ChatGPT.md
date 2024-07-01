---
title: 「开源」Android Studio完美对接ChatGPT
date: '2023-12-30'
tags:
  - - Ai
  - - Android
  - - Java
categories:
  - - 开源项目
  - - 编程开发
  - - 人工智能
keywords:
  - - Java
  - - ChatGPT
  - - Android
description: 这是一个示例文章的描述。
top_img: >-
  https://img.picgo.net/2024/07/01/171171275420240329114554209dc1755056fe73a3.jpg
comments: true
cover: >-
  https://img.picgo.net/2024/07/01/171171275420240329114554209dc1755056fe73a3.jpg
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
abbrlink: c0ee46fe
---
支持多平台服务
- OpenAI ChatGPT 系列模型
- One Api 系列平台服务
- API2D 平台服务
- 其他代理服务
## 效果演示


![](https://img.picgo.net/2024/07/01/171171261920240329114339616ba75b001b4f8389.webp)
![](https://img.picgo.net/2024/07/01/17117126172024032911433731db4c31759c7cfd9a.webp)

## 部署教程

程序基于Android Studio开发，百度自行下载！

找到如下路径：`app/src/main/java/com/example/gpt/MainActivity.java`

搜索方法：`callAPI`
```Java
try {
    // 创建messages数组，包含用户角色和问题内容
    JSONArray messagesArray = new JSONArray();
    JSONObject systemMessage = new JSONObject();
    systemMessage.put("role", "system");
    systemMessage.put("content", "You are ChatGPT, a large language model trained by OpenAI. Follow the user's instructions carefully. Respond using markdown.");
    JSONObject userMessage = new JSONObject();
    userMessage.put("role", "user");
    userMessage.put("content", question);
    messagesArray.put(systemMessage);
    messagesArray.put(userMessage);
    // 构建完整的JSON请求体
    jsonBody.put("model", "gpt-3.5-turbo"); // 模型选择
    jsonBody.put("messages", messagesArray);

}catch (JSONException e) {
    throw new RuntimeException(e);
}

RequestBody body = RequestBody.create(jsonBody.toString(), JSON);
Request request = new Request.Builder()
    .url("https://api.openai.com/v1/chat/completions") // 服务器地址
    .header("Authorization", "Bearer sk-xxx") // 填写你的key
    .header("Content-Type", "application/json")
    .post(body)
    .build();
```
## 下载
GitHub：https://github.com/PastKing/ChatGPT-Android
GitBee：https://gitee.com/past-dust/chat-gpt-android
123盘：https://www.123pan.com/s/7hX0Vv-hHkbv.html
提取码:BO5q