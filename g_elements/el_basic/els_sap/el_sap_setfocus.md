# Фокус ввода

![](<../../../.gitbook/assets/image (279).png>)

Компонент, устанавливающий фокус ввода на выбранном элементе управления.

| Свойство    | Тип                        | Описание                                           |
| ----------- | -------------------------- | -------------------------------------------------- |
| Окно        | String                     | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента | String                     | ID элемента                                        |
| Элемент     | LTools.SAP.Model.SAPUIItem | Ссылка на элемент управления                       |
| Таймаут\*   | Int32                      | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
app.SetFocus("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
app.SetFocus("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
app.SetFocus("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}
{% endtabs %}
