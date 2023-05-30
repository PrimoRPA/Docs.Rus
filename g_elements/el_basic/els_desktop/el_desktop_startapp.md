# Запустить приложение

![](<../../../.gitbook/assets/image (42).png>)

Компонент, запускающий новый процесс.

| Свойство          | Тип                               | Описание                                                                            |
| ----------------- | --------------------------------- | ----------------------------------------------------------------------------------- |
| Тип автоматизации | LTools.Desktop.Model.DesktopTypes | Тип используемой при взаимодействии с приложением автоматизации (UIAUTOMATION, RDP) |
| Приложение\*      | String                            | Имя запускаемого приложения                                                         |
| Аргументы         | String                            | Аргументы процесса. Возможно указать несколько аргументов через пробел: `"arg1 arg2"` |
| Рабочая папка     | String                            | Путь к рабочей папке процесса                                                       |
| Ожидать запуск    | Boolean                           | Ожидать запуск приложения                                                           |
| Переменная        | System.Diagnostics.Process        | Переменная для хранения созданного процесса                                         |

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
