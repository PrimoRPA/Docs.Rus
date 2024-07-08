# Снимок рабочего стола

*Eng: Create Screenshot*

![](<../../../.gitbook/assets/image (124).png>)

Элемент **Снимок рабочего стола** предназначен для создания скриншотов рабочего стола или конкретного запущенного процесса в процессе выполнения автоматизированных задач в Primo RPA Studio. Этот компонент фиксирует текущее состояние экрана, что может быть полезно для отладки, мониторинга и документации.

Если необходимо создать скриншот всего рабочего стола, свойства, относящиеся к процессу, могут быть оставлены пустыми. В случае, когда требуется сделать снимок только определенного процесса, указывается соответствующее имя процесса.

### Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство                    | Тип                        | Описание                                                                                                                        |
| --------------------------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Вывод**                   |                            |                                                                                                                                 |
| Отправить в Оркестратор     | bool                       | Если этот флажок установлен, скриншоты будут отправляться в Оркестратор. Важно отметить, что сообщения активности "Снимок рабочего стола" с установленной галкой "Отправить в Оркестратор" по задумке являются отладочными сообщениями (Debug) и будут видны только при включенном отображении сообщений уровня Debug. |
| Переменная                  | System.Drawing.Bitmap      | Переменная для сохранения изображения                                                                                                                                           |
| **Рабочий стол**            |                            |                                                                                                                                 |
| Заголовок                   | String                     | Заголовок подключаемого приложения                                                                                              |
| Имя процесса                | String                     | Имя процесса                                                                                                                    |
| Область                     | System.Drawing.Rectangle   | Область поиска компонента                                                                                                       |
| Переменная                  | LTools.Desktop.DesktopInst | Переменная, содержащая ссылку на подключенный процесс                                                                           |

### Как использовать

1. Перенесите элемент **Снимок рабочего стола** в свой процесс/проект в Студии.
2. Настройте необходимые свойства, включая `Имя процесса` для указания процесса и `Переменная` для хранения результатов.
3. При необходимости активируйте опцию `Отправить в Оркестратор`, чтобы скриншоты отправлялись в Оркестратор.


###  Пример на Learning 

Для изучения работы с элементом **Снимок рабочего стола**, вы можете скачать обучающий RPA-проект по следующей ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip)

1. Скачайте архив с обучающими материалами с указанной страницы.
2. Распакуйте архив и откройте проект `StudioActivities` в Студии.
3. Найдите процесс `StudioActivities/Ru/Рабочий стол/Снимок рабочего стола.ltw` для изучения работы элемента.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Весь рабочий стол
System.Drawing.Bitmap bmp = LTools.Desktop.DesktopApp.CreateScreenshot(wf);
bmp.Save(@"C:\screen1.png");
//Приложение по заголовку
bmp = app.CreateScreenshot(null, "Test_*");
bmp.Save(@"C:\screen2.png");
//Текущее приложение
bmp = app.CreateScreenshot();
bmp.Save(@"C:\screen3.png");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Весь рабочий стол
bmp = LTools.Desktop.DesktopApp.CreateScreenshot(wf);
bmp.Save("C:\\screen1.png");
#Приложение по заголовку
bmp = app.CreateScreenshot(None, "Test_*");
bmp.Save("C:\\screen2.png");
#Текущее приложение
bmp = app.CreateScreenshot();
bmp.Save("C:\\screen3.png");
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Весь рабочий стол
var bmp = _lib.LTools.Desktop.DesktopApp.CreateScreenshot(wf);
bmp.Save("C:\\screen1.png");
//Приложение по заголовку
bmp = app.CreateScreenshot(null, "Test_*");
bmp.Save("C:\\screen2.png");
//Текущее приложение
bmp = app.CreateScreenshot();
bmp.Save("C:\\screen3.png");
```
{% endtab %}
{% endtabs %}
