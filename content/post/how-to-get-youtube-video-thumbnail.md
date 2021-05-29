---
title: "Как получить миниатюру для YouTube видео"
date: 2021-05-23T19:27:40+04:00
tags:
  - youtube
  - markdown
categories:
  - Web
draft: false
---

Каждое видео YouTube имеет 4 сгенерированных изображения. Их можно найти по следующим адресам:
```
https://img.youtube.com/vi/<insert-youtube-video-id-here>/0.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/1.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/2.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/3.jpg
```
Первая ссылка в списке — полноразмерное изображение, а другие — уменьшенные изображения.<!--more--> Уменьшенное изображение по умолчанию (т. е. один из 1.jpg, 2.jpg, 3.jpg) лежит здесь:
```
https://img.youtube.com/vi/<insert-youtube-video-id-here>/default.jpg
```
Для высококачественной версии миниотюры используйте url-адрес, подобный этим:
```
https://img.youtube.com/vi/<insert-youtube-video-id-here>/hqdefault.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/hq1.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/hq2.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/hq3.jpg
```
Существует также версия миниатюры среднего качества, использующая url-адрес, похожий на эти:
```
https://img.youtube.com/vi/<insert-youtube-video-id-here>/mqdefault.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/mq1.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/mq2.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/mq3.jpg
```
Для стандартной версии определения изображения используйте url-адрес, подобный этим (не всегда существуют):
```
https://img.youtube.com/vi/<insert-youtube-video-id-here>/sddefault.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/sd1.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/sd2.jpg
https://img.youtube.com/vi/<insert-youtube-video-id-here>/sd3.jpg
```
Для версии изображения с максимальным разрешением используйте url-адрес, подобный этому (не всегда существует):
```
https://img.youtube.com/vi/<insert-youtube-video-id-here>/maxresdefault.jpg
```
Для изображения с разрешением 720p используйте следующий адрес (не всегда существует):
```
https://img.youtube.com/vi/<insert-youtube-video-id-here>/hq720.jpg
```
Для вставки YouTube видео в markdown документ используйте код подобный этому:
```
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](https://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)
````

В адресе можно использовать `i3.ytimg.com` вместо `img.youtube.com`.
