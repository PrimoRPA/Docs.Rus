# Приложение 1С (локальная БД)

![](<../../../.gitbook/assets/image (442).png>)

Компонент, производящий подключение к локальной БД 1С.

Перед начало работы установите компоненты 1С (выполните regsvr32 \[Путь к 1С]\comcntrt.dll).

### Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa). Символ `*` указывает на обязательность заполнения.

| Свойство    | Тип                                      | Описание                             |
| ----------- | ---------------------------------------- | ------------------------------------
| **Сервер**  |  |
|Защищенный пароль |SecureString|Защищенный пароль|
| Версия 1С\* | LTools.Office.OneS.Model.AutomationTypes | Версия 1С                            |
| Путь к БД\* | String                                   | Путь к локальной БД 1С (c:\folder\\) |
| Логин\*     | String                                   | Логин пользователя БД                |
| Пароль\*    | String                                   | Пароль пользователя БД               |


## Только код

Пример использования с типом процесса Только код (Code only)

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OneSApp app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "db path", "login", "password");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "db path", "login", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OneSApp.Init(wf, _lib.LTools.Office.OneS.Model.AutomationTypes.V83, "db path", "login", "password");
```
{% endtab %}
{% endtabs %}
