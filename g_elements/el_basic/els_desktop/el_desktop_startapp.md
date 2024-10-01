---
description: Start application
---

# Запустить приложение

![](<../../../.gitbook/assets/image (42).png>)

Элемент запускает процесс.



## Свойства
Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Desktop Anywhere**:

1. **Адрес** *[String]* — адрес сервиса.
1. **Логин** *[String]* — логин сервиса.
1. **Пароль** *[String]* — пароль сервиса.

**Процесс**:

1. **Тип автоматизации** *[LTools.Desktop.Model.DesktopTypes]* — тип используемой при взаимодействии с приложением автоматизации (UIAUTOMATION, RDP).
1. **Приложение\*** *[String]* — имя запускаемого приложения.
1. **Аргументы** *[String]* — аргументы процесса. Возможно указать несколько аргументов через пробел: `"arg1 arg2"`.
1. **Рабочая папка** *[String]* — путь к рабочей папке процесса.
1. **Ожидать запуск** *[Boolean]* — ожидать запуск приложения.


**Вывод**:

1. **Переменная** *[System.Diagnostics.Process]* — переменная для хранения созданного процесса.
1. **Консоль** *[LTools.Desktop.Model.ConsoleApp]* — ссылка на консольное приложение.


## Только код



{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp.Start(wf, "calc", null, @"c:\", LTools.Desktop.Model.DesktopTypes.UIAUTOMATION, true);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Desktop.DesktopApp.Start(wf, "calc", None, "c:\\", LTools.Desktop.Model.DesktopTypes.UIAUTOMATION, True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Desktop.DesktopApp.Start(wf, "calc", null, "c:\\", _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION, true);
```
{% endtab %}
{% endtabs %}
