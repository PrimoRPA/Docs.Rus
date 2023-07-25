# Проговорить сообщение

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (231).png>)

![](<../../../.gitbook/assets/Проговорить сообщение.png>)

Компонент, проговаривающий голосом заданное сообщение.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство      | Тип    | Описание                 |
| ------------- | ------ | ------------------------ |
| Текст запроса | String | Произносимое сообщение   |
| Текст SSML    | String | Сообщение в формате SSML |
| Голос         | String | Используемый голос       |
| Громкость     | Int32  | Громкость голоса         |
| Скорость      | Int32  | Скорость произношения    |

{% tabs %}
{% tab title="C#" %}
```csharp
List<InstalledVoice> ret = LTools.Workflow.PrimoApp.GetVoices(wf);
LTools.Workflow.PrimoApp.Speech(wf, "text", ret[0], 5
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Workflow.PrimoApp.GetVoices(wf)
LTools.Workflow.PrimoApp.Speech(wf, "text", ret[0], 
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Workflow.PrimoApp.GetVoices(wf);
_lib.LTools.Workflow.PrimoApp.Speech(wf, "text", ret[0], 50
```
{% endtab %}
{% endtabs %}
