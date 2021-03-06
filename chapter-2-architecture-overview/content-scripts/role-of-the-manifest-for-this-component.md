### Роль манифеста

Рассмотрим, какие нужно указать параметры в манифесте, чтобы подключить сценарии контента. Во-первых, вам нужно объявить `content_scripts` атрибут, как показано в наведённом примере кода:

```
"content_scripts" : [
    {
        "matches" : ["http://www.google.com/*"],
        "css" : ["mystyles_A.css"],
        "js" : ["jquery.js","myscript_A.js"]
    }
]
```

Указанный атрибут является массивом, со свойствами `matches`, `css`, и `js`. Как видим `css`и `js`являются массивами, содержащие список css и js файлов, которые требуются интегрировать на веб-страницы, с адресом соответствующий правилам указанные в свойстве `matches`.

Так же JavaScript или CSS можно добавить программно используя объект `tabs`\(для это не забудьте предоставить разрешение `activeTab`, для взаимодействия с вкладками\).

Разрешение `activeTab`даёт временный доступ к активной вкладке. Он длиться пока она активна или не будет закрыта.

Чтобы добавить программно CSS или JavaScript к вкладке используются следующие методы:

```
chrome.tabs.insertCSS(integer tabId, object details, function callback)
chrome.tabs.executeScript(integer tabId, object details, function callback)
```

> **Примечание:**  
> Программным добавление JavaScript или CSS файлов не стоит злоупотреблять, используйте только в определённых случаях где без этого невозможно обойтись.

`tabId`– это идентификатор вкладки. Следующий параметр содержит JavaScript код \(css\) или файл, который добавляется.

Ниже рассмотрим пример расширения HelloContentScript, демонстрирующий использование контент сценариев.

##### Листинг 2-11. _Chapter2/HelloContentScript/manifest.json_

```
{
    "manifest_version" : 2,
    "name" : "HelloContentScript",
    "description" : "Расширение для демонстрации контент сценариев",
    "version" : "1.2",
    "content_scripts" : [
        {
            "matches" : ["*://stackoverflow.com/*"],
            "js" : ["content_script.js"]
        }
    ],
    "background" : {
        "scripts" : ["event_script.js"],
        "persistent" : false
    },
    "permissions" : ["activeTab"],
    "browser_action" : {
        "default_icon" : "icon.png"
    }
}
```



