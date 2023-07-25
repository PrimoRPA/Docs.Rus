# Сохранить сообщение

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (46).png>)

![](<../../../.gitbook/assets/Сохранить сообщение Exchange и Outlook.png>)

Позволяет сохранить на диск письмо из электронной почты Outlook. Корректно работает только внутри контейнера [**Приложение Outlook**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_outlook/el\_outlook\_app).

> _Общие свойства элемента описаны в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)_._

| Свойство    | Тип                                                                        | Описание                                   |
| ----------- | -------------------------------------------------------------------------- | ------------------------------------------ |
| Путь\*      | String                                                                     | Путь сохранения файла в формате \*.eml     |
| Сообщение\* | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md) | Сообщение для сохранения в виде переменной |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf);
app.SaveMessage(msg, @"c:\file.msg", LTools.Office.Model.OutlookApp.MessageFileTypes.MSG);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf)
app.SaveMessage(msg, "c:\file.msg", LTools.Office.Model.OutlookApp.MessageFileTypes.MSG)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf);
app.SaveMessage(msg, "c:\\file.msg", _lib.LTools.Office.Model.OutlookApp.MessageFileTypes.MSG);
```
{% endtab %}
{% endtabs %}
