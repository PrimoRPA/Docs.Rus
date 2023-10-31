# Получить из буфера обмена

*Eng: Get from Clipboard*

Элемент позволяет извлекать данные из буфера обмена.

![](<../../../.gitbook/assets/image (367).png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство  | Тип    | Описание          |
| --------- | ------ | ----------------- |
| Результат | Object | Название переменной для хранения полученных данных |
| Как текст | Boolean | Определяет, нужно ли получать данные в виде текста. Если чекбокс установлен, то в свойстве **Формат** можно задать формат текста |
| Формат    | -       | Учитывается только при установке чекбокса **Как текст**. Выберите из выпадающего списка формат, в котором необходимо хранить текст в буфере обмена. По умолчанию указан `Unicode Text` |


## Пример на Learning

RPA-сценарий, демонстрирующий работу элемента, доступен на [Learning](https://github.com/PrimoRPA/Learning). Скачайте проект StudioActivities, откройте его в Студии и выберите процесс `StudioActivities/Ru/Буфер обмена/Копировать-Вставить.ltw` для просмотра. 

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

