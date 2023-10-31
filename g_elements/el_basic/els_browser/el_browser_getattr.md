# Получить атрибут 
_Eng: Get Attribute_

Компонент позволяет получить данные атрибута элемента управления. 

![Get Attribute 2](<../../../.gitbook/assets/image (319).png>)

Для корректной работы требуется:
* поместить компонент внутрь контейнера [**Открыть браузер**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_open) или [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_attach);
* [установить расширение браузера](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install), к которому вы хотите подключиться.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа «Процесс»**:

- **Атрибут**: String. Название атрибута элемента управления. Пример: `"title"`.
- **Таймаут\***: Int32. Предельное время ожидания завершения процесса (в миллисекундах). По умолчанию `10000`. 
- **Шаблон поиска**: String. [Шаблон поиска](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns) элемента управления (то же, что и селектор). Для быстрого формирования шаблона используйте инструмент **Выбрать компонент** ![](<../../../.gitbook/assets/image (553).png>)
- **Элемент**: LTools.WebBrowser.Model.IElementInfo. Переменная со ссылкой на элемент управления. Заполняется, если нужный элемент управления был найден ранее, с помощью компонента **Присутствие элемента**, и сохранен в переменную.

**Группа «Вывод»**:

- **Результат**: String. Переменная для сохранения данных первого найденного атрибута.
- **Результат (массив)**: List\<string>. Переменная для сохранения данных всех найденных атрибутов.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
List<string> att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title");
//Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");		
LTools.Workflow.PrimoApp.AddToLog(wf, att[0]);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска
att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title")
#Элемент
el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");	
LTools.Workflow.PrimoApp.AddToLog(wf, att[0])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
var att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title");
//Элемент
var el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");	
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, att[0]);
```
{% endtab %}
{% endtabs %}
