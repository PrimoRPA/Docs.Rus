# Присутствие элемента

![](<../../../.gitbook/assets/image (205).png>)

Компонент, производящий поиск элемента управления. Компонент корректно работает только внутри контейнера SAP.

| Свойство    | Тип                        | Описание                                             |
| ----------- | -------------------------- | ---------------------------------------------------- |
| ID элемента | String                     | ID элемента                                          |
| Элемент     | LTools.SAP.Model.SAPUIItem | Переменная для хранения ссылки на элемент управления |
| Результат   | Boolean                    | Переменная, хранящая результаты поиска               |
| Таймаут\*   | Int32                      | Предельное время ожидания завершения процесса (мс)   |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUIItem item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}
{% endtabs %}
