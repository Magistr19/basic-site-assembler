# basic-site-assembler #
Выполнил - **Паярели Александр**

## Описание проекта:
Базовая сборка сайта для ускоренной верстки. По мере необходимости, сборка будет редактироваться, дополняться. Для наглядной демонстрации работы сборки можете посетить мой проект, работающий на этой сборке: https://github.com/Magistr19/cat-energy<br/>

## Описание файловой структуры:

source/ <!-- Всю разработку сайта выполнять только в source -->
  | - fonts <!-- Папка для шрифтов. Формата .woff и .woff2 -->
  | - img <!-- Папка для изображений .jpg .png .svg -->
    | - inline-icons <!-- Папка для svg, которые нужно конвертировать в единный спрайт. После выполнения сборки, выдаст этот файл в папке build/img/sprite.svg -->
    | - towebp <!-- Папка для jpg и png, которые нужно конвертировать в webp. После выполнения сборки, выдаст эти файлы в папке build/img/*.webp  -->
  | - js <!-- Папка для скриптов. ___Внимание!___ Сборка не конкатенирует отдельные JavaScript файлы в единный -->
  | -sass <!-- Папка для .scss. Содержит главный style.scss файл, где подключен нормалайзер, переменные, примеси и scaffolding(подключение шрифтов, задание уникальных классов и общие надстройки страницы). ___Внимание!___ Не нужно подключать через @import .scss файлы из папки blocks в style.scss. Сборка сделает это за вас  -->
    | -basic <!-- Содержит основные .scss файлы, общие надстройки страниц. Нужно вручную подключать их в style.scss, порядок подключения важен -->
    | -blocks <!--  Содержит .scss файлы непосредственно вашего сайта. Важно понимать, что при верстке по БЭМ их порядок подключения не важен, соответственно сборщик сам их сконкантенирует -->
  | - index.html <!-- Базовая разметка страницы, все html файлы кидать в корень папки source -->
.editorconfig <!-- Файл с настройками для редактора, внутри инструкция как его подключить -->
.gitattributes <!-- Предоставляет attributes для путей. Лучше не редактировать его -->
.gitignore <!-- Говорит гиту, какие файлы не замечать. Лучше не редактировать его -->
csscomb.json <!-- Настройки для плагина csscomb, которые можно скачать в любой популярный редактор. Автоматически подключается после установки csscomb. -->
gulpfile.js <!-- Описывает как работает сборка. Все содержание закомментированно, чтобы легко можно было туда залезть и поменять на свой вкус что-то -->
package.json <!-- Описывает пакеты, которые были подключены в проект -->
package-lock.json <!-- Описывает зависимости, которые требуют пакеты из package.json. Лучше не редактировать его -->

## Особенности сборки:
Благодаря GULP таск раннера, моя сборка умеет:
1) Автоматически минимизировать изображения jpg, png, svg без потери качества, и конвертировать отдельные изображения в webp с легкой потерей качества
2) Автоматически минимизировать скрипты, стили и html файлы 
3) Поддерживать include шаблонизатор для вставки содержимого одного документа в другой
4) Конвертировать отдельные svg изображения в один спрайт
5) Конвертировать .scss в .css без использования @import в главном .scss файле
6) Отслеживать любые изменения в папке разработки, обновлять браузер при необходимости
7) Работать без прерываний на протяжении всего рабочего процесса


## Запуск сборки

1) Скачайте и установите [Node.js](https://nodejs.org/en/ "Ссылка на оф. сайт Node.js")
2) Скачайте и установите [Git Bash](https://git-scm.com/downloads "Ссылка на скачку Git Bash")
3) Создайте и зайдите в папку для проекта. Нажмите правой кнопкой мыши на пустую область папки и выберите Git Bash Here

![Тут должна была быть картинка-подсказка, но она не загрузилась =*(](https://a.radikal.ru/a27/1810/e3/039fb460e246.png)

4) Загрузите сборку локально себе на компьютер с помощью команды:<br/>
`git clone https://github.com/Magistr19/basic-site-assembler.git .`
5) Обновите версии вспомогательных пакетов, которые были использованные в проекте:<br/>
`npm up`
6) Установите все вспомогательные пакеты, которые были использованные в проекте:<br/>
`npm i`
7) Выполните сборку проекта <br/>
`npm run build`<br/>
В папке проекта появится папка build, которая содержит скомпилированный проект на выпуск в продакшн.<br/>

Для выполнения компиляции и запуска локального сервера с автообновлением браузера и build на изменения, используйте команду `npm start`.<br/>

___Внимание!___ Не редактируйте содержимое папки build. Все изменение вносите в папку разработки - source<br/>
Не удаляйте и не обращайте внимание на файлы:<br/>
_`.gitattributes`, `.gitignore`, `.gulpfile.js`, `package-lock.json`, `package.json`._
