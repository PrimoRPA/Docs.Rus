# Присоединиться к приложению

![](<../../../.gitbook/assets/image (191).png>)

Компонент осуществляет подключение к действующему процессу внешнего приложения. Общие свойства элемента описаны в разделе [Работа с элементами](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements). Утилитарные представлены в таблице ниже.

При нажатии в свойстве **Заголовок** кнопки <img src="../../../.gitbook/assets/14 (1) (2) (1) (1) (1).png" alt="" data-size="line"> появляется селектор для автоматического выбора заголовка приложения. Достаточно кликнуть на окно нужного.

| Свойство             | Тип                               | Описание                                                                                  |
| -------------------- | --------------------------------- | ----------------------------------------------------------------------------------------- |
| ***Рабочий стол***   |                                   |                 |
| Заголовок            | String                            | Заголовок подключаемого приложения                                                        |
| Имя процесса         | String                            | Название процесса запущенного приложения                                              |
| Переменная           | LTools.Desktop.DesktopInst        | Переменная, содержащая ссылку на подключенный процесс                                     |
| Таймаут\*            | Int32                             | Предельное время ожидания завершения процесса (мс)                                        |
| ***Процесс***        |                                   |         |
| Текущий пользователь | bool                              | Признак получения процессов только текущего пользователя                                  |
| Тип автоматизации    | LTools.Desktop.Model.DesktopTypes | Выберите тип автоматизации, который используется для взаимодействия с десктоп-приложением. По умолчанию используется UIAUTOMATION - для приложений, работающих по правилам Win32. Для взаимодействия с приложениями Java, выберите тип Java или Java_ext |
|***Вывод***           |                                   |    |
| Переменная           | LTools.Desktop.DesktopInst        | Переменная вывода, которая сохраняет ссылку на подключенный процесс |

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
