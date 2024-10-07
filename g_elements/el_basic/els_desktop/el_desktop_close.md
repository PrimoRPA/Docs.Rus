# Завершить приложение

*Eng: Close application*

Элемент завершает работу внешнего приложения. Данный элемент работает только внутри контейнера [Присоединиться к приложению](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_attach), в свойствах которого следует указать заголовок приложения/имя процесса.

![](<../../../.gitbook/assets/image (173).png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство  | Тип   | Описание                                           |
| --------- | ----- | -------------------------------------------------- |
| Таймаут\* | Int32 | Предельное время ожидания завершения процесса (мс). По умолчанию `10000` |


##  Пример использования

Пример процесса с работой элемента **Завершить приложение** вы можете найти в нашем публичном репозитории Learning.

1. Скачайте архив с обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте проект `StudioActivities` в Студии.
3. Откройте процесс `StudioActivities/Ru/Рабочий стол/Завершить приложение.ltw`.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Close();	
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.Close()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Close();
```
{% endtab %}
{% endtabs %}
