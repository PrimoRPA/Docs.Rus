# Закладки

![](<../../../.gitbook/assets/image (385).png>)

Элемент, получающий указатель на UI-элемент Закладки.

| Свойство         | Тип                                                          | Описание                                           |
| ---------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| Окно          | String                     | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента      | String                                                       | ID элемента                                        |
| Элемент          | LTools.SAP.Model.SAPUIItem                                   | Ссылка на элемент управления                       |
| Закладки         | [LTools.SAP.Model.SAPUITabStrip](datatypes/sapuitabstrip.md) | Переменная, хранящая ссылку на закладки            |
| Переменная       | [LTools.SAP.Model.SAPUITabStrip](datatypes/sapuitabstrip.md) | Переменная для сохранения ссылки на закладки       |
| Элементы         | List<[LTools.SAP.Model.SAPUITab](datatypes/sapuitab.md)>     | Элементы массива закладок                          |
| Выбрать (ключ)   | String                                                       | Выбрать закладку по ключу                          |
| Выбрать (индекс) | Int32                                                        | Выбрать закладку по индексу                        |
| Таймаут\*        | Int32                                                        | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUITabStrip tabs = app.TabStrip("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
tabs.SelectTab(tabs.Tabs[0].Id);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf);
tabs = app.TabStrip("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
tabs.SelectTab(tabs.Tabs[0].Id)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
var tabs = app.TabStrip("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
tabs.SelectTab(tabs.Tabs[0].Id);
```
{% endtab %}
{% endtabs %}

