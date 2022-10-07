# Запустить макрос

![](<../../../../.gitbook/assets/Запустить макрос Word.png>)

Элемент, выполняющий макрос Word. Не поддерживается на ОС Linux.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство             | Тип                                                               | Описание                                           |
| -------------------- | ----------------------------------------------------------------- | -------------------------------------------------- |
| ***Word***           |                                                                   |                                                    |
| Наименование\*       | String                                                            | Наименование макроса                               |
| Аргументы\*          | List\<object\>                                                    | Аргументы макроса                                  |
| Видимость\*          | Boolean                                                           | Видимость Word                                     |
| ***Вывод***          |                                                                   |                                                    |
| Переменная           | Object                                                            | Сохраняет результат выполнения скрипта             |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, @"c:\folder\file.docx", LTools.Office.Model.InteropTypes.Interop);
app.RunMacro("name");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "c:\folder\file.docx", LTools.Office.Model.InteropTypes.Interop)
app.RunMacro("name")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, @"c:\\folder\\file.docx", _lib.LTools.Office.Model.InteropTypes.Interop);
app.RunMacro("name"
```
{% endtab %}
{% endtabs %}
