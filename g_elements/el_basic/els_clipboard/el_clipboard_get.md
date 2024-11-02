---
description: Get from Clipboard
---


# Получить из буфера обмена

![](<../../../.gitbook/assets/image (367).png>)

Элемент извлекает данные из буфера обмена.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство  | Тип    | Описание          |
| --------- | ------ | ----------------- |
| Как текст | Boolean | Определяет, нужно ли получать данные в виде текста. Если чекбокс установлен, то в свойстве **Формат** можно указать формат текста |
| Формат    | -       | Учитывается только при установке чекбокса **Как текст**. Выберите из выпадающего списка формат, в котором необходимо хранить текст в буфере обмена. По умолчанию задан `Unicode Text` |
| Результат | Object  | Название переменной для хранения данных, полученных из буфера обмена |


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
object obj = LTools.Desktop.DesktopApp.GetFromClipboard(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
obj = LTools.Desktop.DesktopApp.GetFromClipboard(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var obj = _lib.LTools.Desktop.DesktopApp.GetFromClipboard(wf);
```
{% endtab %}
{% endtabs %}

