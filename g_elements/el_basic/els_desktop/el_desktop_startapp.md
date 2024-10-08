---
description: Start application
---

# Запустить приложение

![](<../../../.gitbook/assets/image (42).png>)

Элемент запускает экземпляр приложения рабочего стола в ОС Windows. Поддерживается запуск приложения с входными параметрами (*аргументами*).

К запущенному приложению впоследствии можно подключиться через контейнер [Присоединиться к приложению](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_attach), чтобы иметь возможность взаимодействовать с элементами интерфейса.

## Свойства
Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


**Процесс**:

1. **Приложение\*** *[String]* — имя запускаемого приложения. В значении можно указать только имя исполняемого файла или полный путь до исполняемого файла/ярлыка. Если указан полный путь, то свойство **Рабочая папка** указывать не нужно. Пример: `@"C:\Program Files\Mozilla Firefox\firefox.exe"`.
1. **Рабочая папка** *[String]* — путь к рабочей папке процесса, который указан в свойстве **Приложение**. 
1. **Тип автоматизации** *[LTools.Desktop.Model.DesktopTypes]* — тип используемой автоматизации при взаимодействии с приложением. Доступные значения:
   * `UIAUTOMATION` — значение по умолчанию. Современная технология автоматизации для взаимодействия с приложениями, которые работают по правилам Win32.
   * `UIAUTOMATION_UAI` — рекомендуется использовать в случае, если в режиме UIAUTOMATION не удается получить доступ к нужному приложению.
   * `MSAA` — устаревшая технология Microsoft Active Accessibility. Имеет больше ограничений, чем UIAUTOMATION. 
   * `RDP` — для взаимодействия с приложениями удаленного рабочего стола по протоколу RDP.
   * `JAVA` — для взаимодействия с Java-приложениями.
   * `JAVA_EXT` — для более глубокого взаимодействия с Java-приложениями, 
   * `DESKTOP ANYWHERE` — для взаимодействия с приложениями удаленного рабочего стола через утилиту [Desktop Anywhere](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/desktop-anywhere).
1. **Аргументы** *[String]* — входные аргументы процесса. Возможно указать несколько аргументов через пробел: `"arg1 arg2"`.
1. **Ожидать запуск** *[Boolean]* — определяет, следует ли ожидать запуск приложения. По умолчанию не используется.

**Desktop Anywhere**:

> Свойства этой группы заполняются только в случае, если вы хотите запустить приложение удаленного рабочего стола с использованием утилиты Desktop Anywhere. 

1. **Адрес** *[String]* — адрес сервиса Desktop Anywhere.
1. **Логин** *[String]* — логин сервиса.
1. **Пароль** *[String]* — пароль сервиса.


**Вывод**:

1. **Переменная** *[System.Diagnostics.Process]* — название переменной для хранения созданного процесса.
1. **Консоль** *[LTools.Desktop.Model.ConsoleApp]* — название переменной для хранения ссылки на консольное приложение.


## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Откройте процесс `Ru > Рабочий стол > Запустить приложение.ltw` для просмотра.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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

## См. также
* [Уничтожить процесс](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_kill)
