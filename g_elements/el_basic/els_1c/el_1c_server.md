---
description: 1C Server
---

# Приложение 1С (сервер)

![](<../../../.gitbook/assets/image (440).png>)

Компонент, производящий подключение к серверной БД 1С.

Перед начало работы установите компоненты 1С (выполните regsvr32 \[Путь к 1С]\comcntrt.dll).

## Свойства
Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип                                      | Описание               |
| --------------- | ---------------------------------------- | ---------------------- |
| **1C** |  |
| Версия 1С\*     | LTools.Office.OneS.Model.AutomationTypes | Версия 1С              |
| Адрес сервера\* | String                                   | Адрес сервера 1С       |
|Защищенный пароль  |SecureString  | |
|Имя ИБ 1С |String  |Название информационной базы 1С |
| Путь к БД\*     | String                                   | Путь к серверной БД 1С |
| Логин\*         | String                                   | Логин пользователя БД  |
| Пароль\*        | String                                   | Пароль пользователя БД |


## Только код

Пример использования в процессе с типом Только код

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OneSApp app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OneSApp.Init(wf, LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OneSApp.Init(wf, _lib.LTools.Office.OneS.Model.AutomationTypes.V83, "server", "db_path", "login", "password");
```
{% endtab %}
{% endtabs %}
