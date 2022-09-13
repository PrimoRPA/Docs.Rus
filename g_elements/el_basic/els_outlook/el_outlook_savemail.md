# Сохранить сообщение

![](<../../../../.gitbook/assets/image (815).png>)

![](<../../../../.gitbook/assets/Сохранить сообщение Exchange и Outlook.png>)

Позволяет сохранить на диск письмо из электронной почты Outlook. Корректно работает только внутри контейнера [**Приложение Outlook**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook/el_outlook_app).

> *Общие свойства элемента описаны в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements).*

| Свойство       |Тип                                                                         | Описание                                             | Обязательность | 
| -------------- | ---------------------------------------------------------------------------| ---------------------------------------------------- |----------------|
| Путь           | String                                                                     | Путь сохранения файла в формате \*.eml               |Да              |
| Сообщение      |[LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)  | Сообщение для сохранения                             |Да              |


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

