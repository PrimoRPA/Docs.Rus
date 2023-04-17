# Создать архив

![](<../../../../.gitbook/assets/image (340).png>)

Компонент создает архив файлов.

## Свойства

Все свойства элемента разделены на группы - они выделены в таблице жирным курсивом.\
Символ `*` в названии свойства указывает на обязательность заполнения.\
Символ `@` в примерах значений свойств позволяет не экранировать обратные слеши.

| Свойство     | Тип                              | Описание                                          |
| ------------ | -------------------------------- | ------------------------------------------------- |
| ***Общие***  | | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***Архивирование*** | | | 
| Архив\*       | String                          | Путь к создаваемому архиву. Пример: `@"C:\folder\file.zip"` |
| Путь\*        | String                          | Путь к файлам архива. Пример: `@"C:\folder\"`        |
| Путь к 7-zip\* | String                         | Путь к 7zip.dll. Пример: `@"C:\Program Files\7-Zip\7z.dll"` |
| Формат       | LTools.Data.Model.ArchiveFormats | Формат архива: по умолчанию установлен `Zip`. Чтобы выбрать другое значение, откройте выпадающий список |
| Пароль       | String                           | Пароль архива, если имеется                                  |


## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Data.ArchiveApp.Compress(wf, "Путь к файлам", "Fh[bd", LTools.Data.Model.ArchiveFormats.Zip, "Пароль", "Путь к 7-zip");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Data.ArchiveApp.Compress(wf, "Путь к файлам", "Fh[bd", LTools.Data.Model.ArchiveFormats.Zip, "Пароль", "Путь к 7-zip")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Data.ArchiveApp.Compress(wf, "Путь к файлам", "Fh[bd", _lib.LTools.Data.Model.ArchiveFormats.Zip, "Пароль", "Путь к 7-zip");
```
{% endtab %}
{% endtabs %}
