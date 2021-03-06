## Создание темы для Google Chrome

Тема является особым видом расширения, которые меняют внешние оформление браузера. Они упакованы как обычные расширения, но без JavaScript сценариев и HTML-кода.

Вы можете попробовать темы из Chrome Web Store, перейдя по ссылке [https://chrome.google.com/webstore/category/themes](https://chrome.google.com/webstore/category/themes).

> **Примечание:**  
> Способ загрузки темы ничем не отличается от загрузки расширения.

Создать тему очень легко, для этого потребуется несколько изображений и сконфигурировать файл манифест. На рисунке 4-7 показаны изображения, которые будут использоваться в создаваемой теме, а в листинге 4-7 указан код файла манифеста.

##### Листинг 4-7. _Chapter4/Themes/manifest.json_

```
{
    "manifest_version" : 2,
    "name" : "HelloTheme",
    "version" : "1.2",
    "theme" : {
        "images" : {
            "theme_frame" : "images/theme_frame_golden.png", 
            "theme_toolbar" : "images/theme_toolbar_silver.png",
            "theme_ntp_background" : "images/theme_ntp_background.png",
            "theme_ntp_attribution" : "images/theme_ntp_attribution.png"
        },
        "colors" : {
            "tab_text" : [0,0,0],
            "ntp_text" : [255,255,255],
            "button_background" : [0,0,255] 
        },
        "tints" : { 
            "buttons" : [0.0,0.0,0.0],
            "frame" : [-1.0,-1.0,-1.0],
            "frame_inactive" : [-1.0,-1.0,0.3],
            "frame_incognito" : [-1.0,-1.0,0.2],
            "frame_incognito_inactive" : [-1.0,-1.0,0.0]
        }
    }
}
```

![Рисунок 4-7. Изображения для Темы](/assets/figure-4-7.png)

##### Рисунок 4-7. _Изображения для Темы._

> **Примечание:**  
> SVG файл был добавлен в папку для демонстрации использование его в теме.

Тема поддерживает `image`, `color` и `tint` элементы, которые определяются в атрибуте `theme` файла манифеста \(Листинг 4-7\). Также нужно определить свойства этим элементам. Наиболее часто используемые указаны в списке ниже:

* `theme_frame` – изображение для рамки окна, область, которая находится позади вкладок.
* `theme_toolbar` - изображение для текущей вкладки и панели инструментов.
* `theme_ntp_background` - фонового изображения для страницы новой вкладки.
* `theme_ntp_attribution` - атрибуция для страницы новой вкладки.
* `tab_text` - цвета текста в заголовке текущей вкладки.
* `ntp_text` - цвет всего текста на странице новой вкладки.
* `button_background` – фоновый цвет оконных кнопок \(например, минимизировать, закрыть\)
* `buttons` - оттенок, который применяется к кнопкам на панели инструментов Chrome.
* `frame` - оттенок, который применяется к рамке Chrome.
* `frame_inactive` – оттенок рамки, который применяется, когда окно Chrome неактивно.
* `frame_incognito` – оттенок рамки в режиме инкогнито.
* `frame_incognito_inactive` – оттенок рамки неактивного окна в режиме инкогнито.

![Рисунок 4-8. Страница новой вкладки с применённой темой](/assets/figure-4-8.png)

##### Рисунок 4-8. _Страница новой вкладки с применённой темой._

> **Примечание:**  
> Темы не содержат JavaScript и HTML-кода.

На рисунке 4-8 показана страница новой вкладки с примененной темой. Золотистая рамка окна задана при помощи атрибута `theme_frame`, а фоновое изображения при помощи атрибута `theme_ntp_background`. Чтобы указать изображение для атрибуции используется атрибут `theme_ntp_attribution`.

![Рисунок 4-9. Тема в режиме инкогнито](/assets/figure-4-9.png)

##### Рисунок 4-9. _Тема в режиме инкогнито._

> **Примечание:**  
> Оттенки задаются в формате Hue-Saturation-Lightness \(HSL\), где используются числа с плавающей точкой в диапазоне от 0 до 1.0. Если указано -1.0, то значение не выбрано.

Для режима инкогнито можно задать свои оттенки. На рисунке 4-9 показано, как выглядит рамки окна если задать оттенок при помощи атрибута `frame_incognito` \(Листинг 4-7\). Кроме это, оттенки можно задать и для неактивного окна. Например, на рисунке 4-10 показаны различия между активным окном \(спереди\) и неактивным окном \(позади\).

![Рисунок 4-10. Оттенок для неактивного окна](/assets/figure-4-10.png)

##### Рисунок 4-10. _Оттенок для неактивного окна._



