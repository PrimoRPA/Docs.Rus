# Присоединиться к SAP

![](<../../../.gitbook/assets/image (45).png>)

Компонент, осуществляющий присоединение к открытому SAP Front End.

| Свойство   | Тип                | Описание                                                 |
| ---------- | ------------------ | -------------------------------------------------------- |
| Переменная | LTools.SAP.SAPInst | Переменная для сохранения ссылки на подключенный процесс |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
```
{% endtab %}
{% endtabs %}
