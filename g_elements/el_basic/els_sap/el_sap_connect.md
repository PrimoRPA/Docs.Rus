# Присоединиться к SAP

![](<../../../.gitbook/assets/image (424).png>)

Контейнер, который осуществляет присоединение к открытому SAP Front End, чтобы начать с ним работу. Открыть SAP можно при помощи элемента [**Открыть SAP**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_sap/el_sap_open).

| Свойство   | Тип                | Описание                                                 |
| ---------- | ------------------ | -------------------------------------------------------- |
| ***SAP Front End***             |           |  |
| Имя системы | String            | Имя процесса SAP, который исполняется. Пример: при работе с приложением SAP Logon Pad исполняется файл saplgpad.exe, следовательно, нужно ввести "saplgpad" |
| Переменная | LTools.SAP.SapApp  | Приложение SAP |
| ***Вывод*** |  |  |
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
