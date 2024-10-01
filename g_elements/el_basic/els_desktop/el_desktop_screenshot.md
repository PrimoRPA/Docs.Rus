# Снимок рабочего стола

*Eng: Create screenshot*

![](<../../../.gitbook/assets/image (124).png>)

Элемент **Снимок рабочего стола** предназначен для создания скриншотов рабочего стола или фиксации текущего состояние экрана в процессе выполнения автоматизированных задач в Primo RPA Studio.  

Если необходимо создать скриншот всего рабочего стола, свойства, относящиеся к процессу, могут быть оставлены пустыми. Если требуется сделать снимок только определенного процесса, укажите соответствующее имя процесса.

**Вариант использования:**

1. Перенесите элемент **Снимок рабочего стола** в процесс в Студии.
2. Настройте необходимые свойства, включая `Имя процесса` для указания процесса и `Переменная` для хранения результатов.
3. При необходимости включите свойство `Отправить в Оркестратор`, чтобы скриншоты отправлялись в Оркестратор. Убедитесь, что у вас настроено подключение к Оркестратору.



### Свойства

Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Рабочий стол**:

1. **Заголовок** *[String]* — заголовок подключаемого приложения.
1. **Имя процесса** *[String]* — имя процесса.
1. **Область** *[System.Drawing.Rectangle]* — область поиска компонента.
1. **Переменная** *[LTools.Desktop.DesktopInst]* — название переменной, которая содержит ссылку на подключенный процесс. Если вы указываете ссылку, то свойство **Имя процесса** следует оставить пустым.                  

**Вывод**:

1. **Переменная** *[[System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?view=netframework-4.8)]* — название переменной, в которую сохранится скриншот рабочего стола.
1. **Отправить в Оркестратор** *[Boolean]* — определяет, следует ли отправлять скриншот в Оркестратор в качестве отладочного события робота (Debug). По умолчанию не используется. При включенном параметре отладочное сообщение будет доступно в Оркестраторе только, если включить отображение сообщений уровня Debug в конфигурационном файле агента Оркестратора. Ниже описаны пошаговые действия.



### Отображения отладочных событий (Debug) робота

Для включения отображения сообщений уровня Debug выполните следующие шаги:

1. Откройте файл конфигурации агента: 
   - Стандартное расположение: `C:\Primo\Agent\appsettings.ProdWin.json`.
2. Найдите секцию `MinimumLevel`.
3. Измените значение `Warning` на `Debug` для всех уровней, как показано ниже:

```json
"MinimumLevel": {
    "Default": "Debug",
    "Override": {
        "System": "Debug",
        "Microsoft": "Debug",
        "Microsoft.EntityFrameworkCore": "Debug",
        "Microsoft.AspNetCore": "Debug"
    }
}
```

4. Сохраните изменения в файле конфигурации.
5. Перезапустите службу для применения изменений.


###  Пример использования элемента

Пример процесса с ипользованием элемента **Снимок рабочего стола** доступен в нашем публичном репозитории Learning. 

1. [Скачайте](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip) архив с обучающими материалами в Learning.
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


