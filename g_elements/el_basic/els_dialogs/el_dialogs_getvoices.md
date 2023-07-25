# Получить голоса

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (231).png>)

![](<../../../.gitbook/assets/Получить голоса.png>)

Компонент, получающий массив доступных в системе голосов.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство | Тип                                           | Описание                                                       |
| -------- | --------------------------------------------- | -------------------------------------------------------------- |
| Голоса   | List\<System.Speech.Synthesis.InstalledVoice> | Переменная, в которую нужно сохранить массив доступных голосов |

{% tabs %}
{% tab title="C#" %}
```csharp
List<InstalledVoice> ret = LTools.Workflow.PrimoApp.GetVoices(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Workflow.PrimoApp.GetVoices(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Workflow.PrimoApp.GetVoices(wf);
```
{% endtab %}
{% endtabs %}
