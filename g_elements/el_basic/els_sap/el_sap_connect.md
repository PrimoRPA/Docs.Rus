# Присоединиться к SAP

![](<../../../.gitbook/assets/image (424).png>)

Контейнер осуществляет присоединение к открытому SAP Front End, чтобы начать с ним работу.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство   | Тип                | Описание                                                 |
| ---------- | ------------------ | -------------------------------------------------------- |
| ***SAP Front End***             |           |  |
| Имя системы | String            | Имя системы. Необязательно для заполнения |
| Переменная  | [LTools.SAP.SAPInst](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_sap/datatypes/sapinst) | Указывается, если в одном процессе Вы используете несколько элементов присоединения к SAP. Например, в первом элементе Вы сохранили ссылку на подключенный процесс в переменной вывода, а во втором указали ее в этом поле для более быстрого присоединения |
| ***Вывод*** |  |  |
| Переменная | [LTools.SAP.SAPInst](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_sap/datatypes/sapinst) | Переменная для сохранения ссылки на подключенный процесс. В дальнейшем может использоваться либо в другом элементе подключения, либо в скриптинге - SAP UI Scripting |

Имя системы можно найти в свойствах для системной записи:

![](<../../../.gitbook/assets/Имя системы.png>)


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
