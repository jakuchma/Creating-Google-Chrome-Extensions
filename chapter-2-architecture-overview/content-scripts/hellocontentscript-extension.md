### Расширение HelloContentScript

Данное расширение подключает контент скрипты с помощью параметра манифеста `content_scripts`, а также программно через событие.

Рассмотрим первый способ. В листинге 2-11 для добавления скриптов задан параметр `matches`. Где указан шаблон начиняющийся с символа звездочка \(\*\). Она означает, что адрес может начинаться с HTTP, HTTPS, или иметь другого значения. Аналогичная, звездочка находится в конце шаблона, что означает за именем хоста stackoverflow.com может следовать любой путь. Результат добавления контент сценария \(content\_script.js\) показано на рисунке 2-16.

![Рисунок 2-16. Добавление контент сценария](/assets/figure-2-16.png)

##### Рисунок 2-16. _Добавление контент сценария._

##### Листинг 2-12. _Chapter2/HelloContentScript/event\_script.js_

```
//region {переменные и функции}
var consoleGreeting = "Hello World! - from event_script.js";
var cssCode = "a {text-decoration:underline !important;}";
cssCode += "div {background-color:#999 !important;}";
var javascriptCode = "var imgElement = document.createElement('img');";
javascriptCode += "imgElement.src = 'http://placehold.it/350x150';";
javascriptCode += "document.body.appendChild(imgElement);";
//end-region

//region {выполнение}
console.log(consoleGreeting);
chrome.browserAction.onClicked.addListener(function(tab) {
    chrome.tabs.insertCSS(
        {
            //Для подключения CSS файла нужно указать
            //file : "mystyles.css",
            code : cssCode
        },
        function() {
            console.log("CSS inserted!");
        }
    );
    chrome.tabs.executeScript(
        {
            //Для подключения JavaScript файла нужно указать
            //file : "content_script.js",
            code : javascriptCode
        },
        function() {
            console.log("JavaScript executed!");
        }
    );
});
//end-region
```

Добавление кода выполняется при помощи слушателя `onClicked`компонента Browser-Action \(смотри листинге 2-12\). В функции слушателе для вставки стилей используется метод `insertCSS`, а для JavaScript кода - `executeScript`. Результат работы расширения показан на рисунке 2-17 и 2-19, а на рисунке 2-18 добавлены только стили. За пример взята страница [www.example.org](http://www.example.org/).

![Рисунок 2-17. HelloContentScript: Работа в фоне](/assets/figure-2-17.png)

##### Рисунок 2-17. _HelloContentScript: Работа в фоне._

![Рисунок 2-18. HelloContentScript: Работа в фоне](/assets/figure-2-18.png)

##### Рисунок 2-18. _HelloContentScript: Работа в фоне._

![Рисунок 2-19. HelloContentScript: Работа в фоне](/assets/figure-2-19.png)

##### Рисунок 2-19. _HelloContentScript: Работа в фоне._

> **Примечание:**  
> Для большего ознакомления с атрибутом Match предлагаем перейти по адресу [https://developer.chrome.com/extensions/match\_patterns](https://developer.chrome.com/extensions/match_patterns).

После нажатия кнопки расширения HelloContentScript на панели задач, слушатель `onClicked `добавляет сгенерированные css стили и JavaScript код. Переменная `cssCode `содержит код CSS, который в ссылках добавляет подчеркивание, а для всех div устанавливает цвет фона. Переменная `javascriptCode `содержит JavaScript код, добавляющий на страницу изображение.

