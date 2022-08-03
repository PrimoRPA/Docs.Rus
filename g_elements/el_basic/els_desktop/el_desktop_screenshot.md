# Снимок рабочего стола

![](<../../../.gitbook/assets/image (124).png>)

Компонент, создающий снимок рабочего стола. В случае, если нужно сделать снимок какого-либо запущенного процесса, указывается процесс. Если нужен снимок всего рабочего стола, свойства, относящиеся к процессу, не заполняются.

| Свойство     | Тип                        | Описание                                              |
| ------------ | -------------------------- | ----------------------------------------------------- |
| Заголовок    | String                     | Заголовок подключаемого приложения                    |
| Имя процесса | String                     | Имя процесса                                          |
| Область      | System.Drawing.Rectangle   | Область поиска компонента                             |
| Переменная   | LTools.Desktop.DesktopInst | Переменная, содержащая ссылку на подключенный процесс |
| Переменная   | System.Drawing.Bitmap      | Переменная для сохранения изображения                 |

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
