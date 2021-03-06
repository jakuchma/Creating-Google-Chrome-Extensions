#### Различия в Browser-Action и Page-Action

В общем Browser-Action представляет собой действие для всех веб-страниц, а Page-Action выполняется для конкретной веб-страницы. Так как это рекомендации от Chrome, и в общем функциональностью данные действия не отличаются, соответственно можно использовать как Browser-Action, так и Page-Action. Но все, таки, с точки зрения API и архитектуры, существуют определённые ограничения и различия, что подталкивает при разработке расширения использовать эти два действия в соответствующих случаях.

После объявления в манифесте Browser-Action, он всегда виден на панели инструментов. Что касается Page-Action, то для отображения в браузере, нужно вызвать в сценарии \(за исключением сценария контента\) метод `chrome.pageAction.show(tabId)`, как показано в листинге 2-7 и 2-8. В дополнение к этому, для отображения Page-Action может быть использован метод `chrome.declarativeContent`.

> **Примечание:**  
> По своей природе, каждая вкладка имеет свой уникальный идентификатор. Кроме того, они представлены типом `Tab`, который имеет множество различных свойств. Основные их них это `id`, `active `и `url`. Полный список свойств доступен по ссылке [https://developer.chrome.com/extensions/tabs\#type](https://developer.chrome.com/extensions/tabs#type).



