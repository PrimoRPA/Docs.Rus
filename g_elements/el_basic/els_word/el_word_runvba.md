# Запустить VBA

![](<../../../../.gitbook/assets/Запустить VBA Word.png>)

Элемент, выполняющий скрипт VBA в Word. Не поддерживается на ОС Linux.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство             | Тип                                                               | Описание                                           |
| -------------------- | ----------------------------------------------------------------- | -------------------------------------------------- |
| ***Word***           |                                                                   |              |
| Файл\*               | String                                                            | Путь к файлу скрипта                               |
| Функция\*            | String                                                            | Имя функции VBA                                    |
| Аргументы\*          | [List<object>                                                     | Аргументы скрипта                                  |
| Видимость\*          | Boolean                                                           | Видимость Word                                     |
| ***Вывод***          |                                                                   |              |
| Переменная           | Object                                                            | Сохраняет результат выполнения скрипта             |

  
{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, @"c:\folder\file.docx", LTools.Office.Model.InteropTypes.Interop);
object data = app.RunVBA(@"c:\file.vba", "func");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "c:\folder\file.docx", LTools.Office.Model.InteropTypes.Interop)
data = app.RunVBA("c:\file.vba", "func")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, @"c:\\folder\\file.docx", _lib.LTools.Office.Model.InteropTypes.Interop);
var data = app.RunVBA("c:\\file.vba", "func");
```
{% endtab %}
{% endtabs %}
