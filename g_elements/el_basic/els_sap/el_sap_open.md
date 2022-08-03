# Открыть SAP

![](<../../../.gitbook/assets/image (361).png>)

Компонент, осуществляющий подключение к SAP Front End.

| Свойство           | Тип                | Описание                                                 |
| ------------------ | ------------------ | -------------------------------------------------------- |
| Соединение\*       | String             | Наименование соединения в SAP Logon                      |
| Клиент\*           | String             | Номер клиента (000-999)                                  |
| Логин\*            | String             | Логин пользователя                                       |
| Пароль\*           | String             | Пароль пользователя                                      |
| Язык подключения\* | String             | Язык подключения                                         |
| Переменная         | LTools.SAP.SAPInst | Переменная, содержащая ссылку на подключенный процесс    |
| Переменная         | LTools.SAP.SAPInst | Переменная для сохранения ссылки на подключенный процесс |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf, "test2", "001", "DEVELOPER", "Appl1ance", "en");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf, "test2", "001", "DEVELOPER", "Appl1ance", "en")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf, "test2", "001", "DEVELOPER", "Appl1ance", "en");
```
{% endtab %}
{% endtabs %}
