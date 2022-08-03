# Эмуляция спецкнопки

![](<../../../.gitbook/assets/image (364).png>)

Компонент, производящий эмуляцию нажатия спецкнопки.

| Свойство     | Тип                       | Описание                                           |
| ------------ | ------------------------- | -------------------------------------------------- |
| Спецкнопки\* | LTools.SAP.Model.SAPVKeys | Нажимаемые спецкнопки                              |
| Таймаут\*    | Int32                     | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
app.HotKeySimulate(LTools.SAP.Model.SAPVKeys.CtrlShiftF1, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
app.HotKeySimulate(LTools.SAP.Model.SAPVKeys.CtrlShiftF1, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
app.HotKeySimulate(_lib.LTools.SAP.Model.SAPVKeys.CtrlShiftF1, 10000);
```
{% endtab %}
{% endtabs %}
