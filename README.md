
# <span style="color:red;">bespoke</span>-<span style="color:blue">scroll</span>-<span style="color:green">bar</span>

![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) ![Webpack](https://img.shields.io/badge/webpack-%238DD6F9.svg?style=for-the-badge&logo=webpack&logoColor=black)

Для поэкранного скролла лендинга часто использутся библиотеки, которые могут блокировать прокрутку блоков внутри страницы. В таких случаях попытка проскролить содержимое такого блока приведет только к перелистыванию страницы. Данный плагин устраняет такую проблему и дает возможность кастомизировать как внешний вид полосы прокрытки, так и ее положение рядом с блоком.

## Подключение

Скачать style-bespoke-scroll-bar-1.0.css и js-bespoke-scroll-bar-1.0.js.

Стили необходимо размести в блоке `<head>` в самом конце списка стилей:    
```html
<link rel="stylesheet" href="files/style-bespoke-scroll-bar-1.0.css">
```
Подключение скрипта сделать перед закрывающим тегом `<body>`, но так, чтобы код для подключения был ниже:
```html
<script src="js/js-bespoke-scroll-bar-1.0.js"></script>
```

## Инициализация

Для инициализации необходимо разместить вызов функции в управляющем скрипте. Скопируйте код с минимальным набором опций:
```js
bespokeScrollBar({
    selectorAria: ".content__wrap",
    widthInput: 5,
})
```
Где `".content__wrap"` это селектор обертки, внутри которой расположен контент, который необходимо скролить. Плагин будет искать все блоки с указанным селектором и если внутри каждого из находится контент, и его высота больше обертки, то скрипт применится. Пример HTML разметки:
```html
<article class="content__wrap">
    <h2>Пример блока с контентом</h2>
    <div class="content__description">
         <!-- Тут много  контента ) -->
    </div>
</article> 
```
> **⚠ Важно:** Ограничение стилями по высоте для контента внутри блока может привести, что скрипт не применится

### <a href="https://maksbmt.github.io/demo-bespoke-scroll-bar/" target="_blank" style="display:block; width:150px;margin:0 auto;">ДЕМО</a>

## Описание опций

|Ключ    |Тип   | Дефолтное&nbsp;значение |  Обязательно или нет  | Описание |
| :---:  | :---: | :-----------: | :---: | :--- |
|selectorAria| String | - | Обязательное поле | Селектор обертки внутри которой должен скролится контент |  
|widthInput| Number | 5 | Необязательное | Значение определяет толщину бегунка в пикселях. Если его не указать, то применится дефолтное и толщина будет 5px |
| thumbBackground | String | "blueviolet" | Необязательное | Ключ определяет цвет бегунка. Допустимы любые форматы, которые читает css свойство background. Например: "#222666", "rgba(175, 252, 65, 1)", "red" |
| trackBackground | String | "rgba(202, 94, 94,&nbsp;0.7);" | Необязательное поле | Ключ определяет цвет поля скролл бара |
| right | Number | 0 | Необязательное | Определяет положение бегунка относительно правого края обертки. При значении 0 - скролл бар будет вплотную примыкать к правому краю. Положительные значения отодвигают вправо. Отрицательные - влево и может располагать скролл бар визуально внутри обертки. **Важно:** *расстояние считается от правого края обертки до левого края скролл бара*. |
|borderRadius| Number | 0 | Необязательное | Ключ определяет border-radius для скролл бара |
|stripHeight| Number | 100 | Необязательное поле | Величина в процентах, которая определяет сколько должен занимать скролл бар. Все поле - 100, Если, к примеру, 80 - то будет занято 80% возможной высоты. Скролл бар при этом выставляется прмерно по середине |
|customTransformY| Number | 100 | Необязательное поле | Значение используется для свига по оси Y скролл бара. Подбирается в ручную через консоль разработчика. Теоретическое нормально положение - 50. Уменьшение приводит к сдвигу вверх, уменьшение - вниз. |
|isStrip| Boolean | true | Необязательное | Ключ запрещает/разрешает рендеринг скролл бара. Используется, когда нужно воостановить скролл внутри блока, но по дизайну скролл бар не нужен |
|isScroll| Boolean | true | Необязательное | Не всегда нужно проводить манипуляции для воостановления скрола внутри блока. Возможны ситуации, когда необходим только кастомный скролл бар - для этого ключ isScroll необходимо поставить в значение false |

