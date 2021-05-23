---
title: "Шрифты Google Fonts на своем сервере"
date: 2020-05-24T14:31:17+04:00
tags:
  - fonts
  - google
  - css
categories:
  - Web
draft: false
---

Я использую свободные шрифты с [Google Fonts](https://fonts.google.com) у себя на сайте. Google Fonts предоставляет CDN, хранит шрифты у себя и отдает CSS файл в зависимости от user-agent пользователя. Однако CSS и шрифты размещаются на разных доменах и при первой загрузке сайта, пока шрифты еще не в кэше, теряется время на два дополнительных соединения. Пока грузится шрифт текст отрисовывается системным и после этого заменяется на необходимый из @font-face. Происходит так называемое мерцание шрифта.<!--more--> 
Я пробывал открыть соединение с `fonts.gstatic.com` заранее, чтобы сэкономить время на втором подключении позже:
```
<link href="https://fonts.gstatic.com" rel="preconnect" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inconsolata&family=Play&display=swap" rel="stylesheet">
```
Задерка уменьшилась, но мерцание шрифта осталось.

Лицензии используемых мной шрифтов позволяет хранить их на своем сервере, и я загрузил шрифты с помощью [`google-webfonts-helper`](https://github.com/majodev/google-webfonts-helper). Я забрал только формат woff2, который используют большинсво современных браузеров. Также я не стал скачивать ext-шрифты. В старых браузерах будут отображатся системные шрифты. Используемый мной css-файл:
```
/* latin monospace for code */
@font-face {
  font-family: 'Inconsolata';
  font-style: normal;
  font-weight: 400;
  font-stretch: normal;
  font-display: swap;
  src: url('../fonts/inconsolata-v19-latin-regular.woff2') format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}

/* latin & cyrillic */
@font-face {
  font-family: 'Play';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: local('Play Regular'), local('Play-Regular'), url('../fonts/play-v11-latin_cyrillic-regular.woff2') format('woff2') format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD, U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
```
