---
title: C++Qt开发的新玩具：OpenAI + TTS
date: '2024-4-8'
tags:
  - - Ai
  - - C++
categories:
  - - 编程开发
keywords:
  - - TTS
  - - Qt
  - - OpenAi
description: 这是一个示例文章的描述。
top_img: https://pan.ltde.cn/directlink/1/image/2024/04/17132353802024041602430081.png
comments: true
cover: https://pan.ltde.cn/directlink/1/image/2024/04/17132353802024041602430081.png
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
abbrlink: 2bd61f0f
---

## 开发工具
- 集成开发环境（IDE）：Qt Creator
## 技术栈
- 开发语言：C++
- UI 框架：Qt
- 网络通信：QNetworkAccessManager
- JSON 处理：QJsonDocument
- 用户界面：Qt Widgets
## 程序介绍

![](https://pan.ltde.cn/directlink/1/image/2024/04/17132353802024041602430081.png)
![](https://pan.ltde.cn/directlink/1/image/2024/04/17132354012024041602432130.png)
这里生成成功就在可执行程序的根目录

## 核心代码
```C++
void Widget::toRequest(QString &urlService,QString &strKey,QString &strText, const QString &filePath){
    QUrl url(urlService);
    QNetworkRequest request(url);

    //请求头
//    QString strNew = "Bearer ";
//    strNew.append(strKey);
//    qDebug()<<strNew;
    QByteArray strNew;
    strNew = "Bearer " + strKey.toUtf8(); // 转换为 QByteArray
    request.setRawHeader("Authorization",strNew);
    request.setHeader(QNetworkRequest::ContentTypeHeader,"application/json");
    //请求体
    QJsonObject json;
    json.insert("model","tts-1-hd");
    json.insert("voice","alloy");
    json.insert("response_format","mp3");
    json.insert("speed",1);
    json.insert("input",strText);
    QJsonDocument doc(json);
    QByteArray data = doc.toJson();

    //发送请求
    QNetworkReply *reply = manager->post(request,data);
    //等待请求结果
    QObject::connect(reply,&QNetworkReply::finished,this, [this, reply,filePath](){
        if(reply->error() == QNetworkReply::NoError){
            //请求成功，保存音频
            QFile file(filePath);
            if(file.open(QIODevice::WriteOnly)){
                file.write(reply->readAll());
                file.close();
                 QMessageBox::information(this, "成功", "音频生成成功，文件已保存。");
                qDebug()<<"音频生成成功";
            }else{
                 QMessageBox::critical(this, "错误", "文件无法保存。");
            }
        }else{
            qDebug()<<"音频生成失败！请检查网络、地址、Key/Token是否出错！！！";
            QMessageBox::critical(this, "失败", "音频生成失败！请检查网络、地址、Key/Token是否出错！！！");
        }
        reply->deleteLater();
    });
}
```