# Отправить в буфер обмена
*Eng: Copy to Clipboard*

Элемент предназначен для отправки текста в буфер обмена.

![](<../../../.gitbook/assets/image (376).png>)

## Свойства
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство | Тип    | Описание                                        |
| -------- | ------ | ----------------------------------------------- |
| Текст    | String | Текст, который будет отправлен в буфер обмена. Пример: `"test text"` |


## Пример на Learning

RPA-сценарий, демонстрирующий работу элемента, доступен на [Learning](https://github.com/PrimoRPA/Learning). Скачайте проект StudioActivities, откройте его в Студии и выберите процесс `StudioActivities/Ru/Буфер обмена/Копировать-Вставить.ltw` для просмотра. 

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

