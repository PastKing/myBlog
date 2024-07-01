---
title: 「开源」基于PyQT开发的MP3音乐下载器
date: 2024-1-18
tags:
  - - Python
  - - 音乐
categories:
  - - 软件分享
  - - 开源项目
keywords:
  - - Mp3
  - - 音乐下载器
description: 这是一个示例文章的描述。
top_img: 'https://s21.ax1x.com/2024/07/01/pkcqfjf.png'
comments: true
cover: 'https://s21.ax1x.com/2024/07/01/pkcqfjf.png'
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
abbrlink: c2a933c4
---
本项目基于Python语言开发，采用PyQt5图形界面库开发，具有直观的用户界面和丰富的功能。

## 主要特点
- 搜索音乐：用户可以通过输入歌曲名称，在应用中进行音乐搜索。搜索结果将以表格形式呈现，包括歌曲的ID、标题、歌手、封面图片和下载按钮。
- 显示搜索结果：搜索结果以表格的形式展示，便于用户浏览和选择。每行的封面图片和下载按钮使得用户可以更直观地了解和操作搜索到的歌曲。
- 下载音乐：用户可以点击下载按钮，将所选歌曲以MP3文件的形式保存到本地。下载过程会在后台进行，不会影响用户继续搜索和操作其他歌曲。
- 快速响应：应用程序采用多线程处理网络请求和文件下载，确保用户能够快速获取搜索结果和下载音乐，提供良好的用户体验。
## 注意事项
- 请确保您的计算机已经安装了PyQt5库和requests库。
- 下载的音乐文件将保存在根目录下的PastKing文件夹中，请确保该文件夹存在或者有写入权限。
- 本程序已用过pyinstaller打包，非二次开发双击即可启动！
## 截图
![](https://s21.ax1x.com/2024/07/01/pkcq7Nj.md.png)
部分代码
```Python
def search_music(self):
    keyword = self.search_input.text()
    if keyword:
        self.worker = Worker(keyword)
        self.worker.result_received.connect(self.show_search_results)
        self.worker.start()

        def show_search_results(self, result):
            self.result_table.setRowCount(0)  # 清空表格内容

            if result and 'data' in result and len(result['data']) > 0:
                for song in result['data']:
                    row_position = self.result_table.rowCount()
                    self.result_table.insertRow(row_position)

                    # 显示歌曲信息
                    self.result_table.setItem(row_position, 0, QTableWidgetItem(str(song['songid'])))
                    self.result_table.setItem(row_position, 1, QTableWidgetItem(song['title']))
                    self.result_table.setItem(row_position, 2, QTableWidgetItem(song['author']))

                    # 显示封面
                    pixmap = self.get_cover_image(song['pic'])
                    label_cover = QLabel(self)
                    label_cover.setPixmap(pixmap)
                    label_cover.setAlignment(Qt.AlignCenter)
                    self.result_table.setCellWidget(row_position, 3, label_cover)

                    # 下载按钮
                    download_button = QPushButton('下载', self)
                    download_button.clicked.connect(lambda _, s=song: self.download_music(s['url'], f"{s['title']}-{s['author']}-{self.get_timestamp()}"))
                    self.result_table.setCellWidget(row_position, 4, download_button)
```
## 下载

123盘：https://www.123pan.com/s/7hX0Vv-mJkbv.html
蓝奏云：https://xcyp.lanzoux.com/iyzDf1lh9hpg

