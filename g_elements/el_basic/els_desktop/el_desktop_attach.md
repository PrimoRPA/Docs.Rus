# Присоединиться к приложению

![](<../../../.gitbook/assets/image (191).png>)

Компонент, осуществляющий подключение к действующему процессу внешнего приложения.

При нажатии кнопки <img src="../../../.gitbook/assets/CapturePattern.png" alt="" data-size="line"> появляется селектор для автоматического выбора заголовка приложения. Достаточно кликнуть на окно нужного.

| Свойство             | Тип                               | Описание                                                                                  |
| -------------------- | --------------------------------- | ----------------------------------------------------------------------------------------- |
| Тип автоматизации    | LTools.Desktop.Model.DesktopTypes | Тип используемой при взаимодействии с приложением автоматизации (UIAUTOMATION, RDP, JAVA) |
| Текущий пользователь | bool                              | Признак получения только процессов текущего пользователя                                  |
| Заголовок            | String                            | Заголовок подключаемого приложения                                                        |
| Имя процесса         | String                            | Имя процесса                                                                              |
| Переменная           | LTools.Desktop.DesktopInst        | Переменная, содержащая ссылку на подключенный процесс                                     |
| Переменная           | LTools.Desktop.DesktopInst        | Переменная для сохранения ссылки на подключенный процесс                                  |
| Таймаут\*            | Int32                             | Предельное время ожидания завершения процесса (мс)                                        |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, "Calc*", null, 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, "Calc*", None, 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Desktop.DesktopApp.Init(wf, "Calc*", null, 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
```
{% endtab %}
{% endtabs %}

