---
description: Keyboard layout
---


# Раскладка

![](<../../../.gitbook/assets/image (83).png>)

Элемент осуществляет смену раскладки клавиатуры.


## Свойства
Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Процесс:**

1. **Раскладка** *[String]* — раскладка для установки. По умолчанию `"ru-RU"`.
1. **Новое ядро** *[Boolean]* — определяет, следует ли использовать новое ядро для смены раскладки. По умолчанию не используется.
1. **Горячая клавиша** — сочетание клавиш для смены языка. Доступные значения:
   * `Alt Shift` — по умолчанию.
   * `Ctrl Shift`.
   * `Win Space`. 
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса, указывается в миллисекундах. По умолчанию `10000`.

**Вывод:**

1. **Раскладки** *[List\<String>]* — название переменной для хранения списка имеющихся раскладок.
1. **Раскладка** *[String]* — название строковой переменной для хранения текущей раскладки клавиатуры. 



## Пример использования

Пример использования элемента **Раскладка** можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Откройте процесс `Ru > Рабочий стол > Раскладка.ltw` для просмотра.



## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SwitchLayout("ru-RU", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SwitchLayout("ru-RU", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SwitchLayout("ru-RU", 10000);
```
{% endtab %}
{% endtabs %}
