---
description: Copy to Clipboard
---


# Отправить в буфер обмена

Элемент предназначен для отправки текста в буфер обмена.

![](<../../../.gitbook/assets/image (376).png>)

## Свойства
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство | Тип    | Описание                                        |
| -------- | ------ | ----------------------------------------------- |
| Текст    | String | Текст, который будет отправлен в буфер обмена. Пример: `"test text"` |


## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте проект из папки **StudioActivities** в вашей Студии.
3. Откройте процесс `StudioActivities > Ru > Буфер обмена > Копировать-Вставить.ltw`.



## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp.SendToClipboard(wf, "text");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Desktop.DesktopApp.SendToClipboard(wf, "text")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Desktop.DesktopApp.SendToClipboard(wf, "text");
```
{% endtab %}
{% endtabs %}

