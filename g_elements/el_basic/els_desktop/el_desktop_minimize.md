---
description: Minimize window
---


# Свернуть окно

![](<../../../.gitbook/assets/image (214).png>)

Элемент сворачивает окно приложения. Для корректной работы поместите элемент **Свернуть окно** в контейнер [Присоединиться к приложению](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_attach), который устанавливает подключение к указанному приложению рабочего стола.


## Свойства
Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

* **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса, указывается в миллисекундах. По умолчанию `10000`.



## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Откройте процесс `Ru > Рабочий стол > Активировать Свернуть Развернуть Восстановить.ltw` для просмотра.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Minimize();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.Minimize()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Minimize();
```
{% endtab %}
{% endtabs %}
