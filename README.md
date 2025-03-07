# Test task Banki.shop

# Open a website:


[WebSite](https://testtask-bunkishop-oniari.netlify.app/)


# Description

```
Test assignment for Banki.shop on Vue 2.
```

# Requirements

```
Vue 2 (Options API)
Node.js 16+
Webpack или Gulp для сборки
Поддержка PixelPerfect верстки
Адаптивность до 360px
Корректное отображение во всех популярных браузерах
```

# Техническое задание:

https://disk.yandex.ru/i/TKbzDFTsRZ4GmQ

https://docs.yandex.ru/docs/view?url=ya-disk-public%3A%2F%2FrOs0forGT9WNCEOVoSEAvsYicfwh5ogClpbDh25y%2BonBTPQkk%2FoULBWJhLyyvyMGtFP6gwbjvtaafTptcua4SA%3D%3D&name=%D0%A2%D0%B5%D1%81%D1%82%D0%BE%D0%B2%D0%BE%D0%B5%20%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5.docx&nosw=1

Макет Figma:

https://www.figma.com/file/6LxPDEsauEGanhR2nDW68X/Banki.shop?node-id=0%3A1

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### requirements

``
Необходимо сверстать макет страницы интернет-магазина:
https://www.figma.com/file/6LxPDEsauEGanhR2nDW68X/Banki.shop?node-id=0%3A1
Технические требования:

- при выполнении тестового задания использовать Vue2 (Options API)
- можно использовать Typescript
- верстка должна максимально соответствовать предоставленному макету. Желательно
  PixelPerfect
- респонсив до 360px (дизайн на свое усмотрение)
- результат должен корректно отображаться во всех популярных браузерах
- при работе над заданием обязательно использование средств автоматизации (webpack или
  gulp). Конфигурация должна корректно работать на 16 версии Node.js

  Требования к приложению - реализовать следущий функционал:

  1 Строка поиска
  При ввода текста в строке поиска должен происходить поиск по названиям позиций.
  Лишние карточки должны исчезать/скрываться.

  2 Кнопка "купить"
  При нажатии на кнопку:

- она должна менять состояние, на 2 сек, на "обрабатывается"
- после "обрабатывается" переходить в состояние "в корзине"
  Отображение состояний визуально оформить, напр. "preloader icon", "purchase icon", "checked
  icon", и т.п.
  Дизайн/стиль продумать самостоятельно.

  3 Сохранение состояния позиций
  После перезагрузки страницы, состояния позиций (в корзине он или нет) должно сохраняться.

  4 Подробное описание позиции
  При клике на название/изображение товара должно открываться модальное окно с карточкой
  товара.
  В карточке должны быть:

- краткое описание позиции
- цена
- слайдер, содержащий 2-4 изображения
  Дизайн модального окна продумать самостоятельно.
  Код приложения должен быть размещен на gihub/gitlab/bitbucket.
  Процесс билдинга и запуска проекта должен быть описан в README.
  Также можно выложить проект на хостинг, и прикрепить ссылку на работающее приложение в
  README.md или e-mail.
  ``
