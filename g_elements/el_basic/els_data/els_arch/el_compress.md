# Создать архив

![](<../../../../.gitbook/assets/image (161).png>)

Компонент, создающий новый архив файлов.

| Свойство     | Тип                              | Описание                                          |
| ------------ | -------------------------------- | ------------------------------------------------- |
| Архив        | String                           | Путь к создаваемому архиву (c:\folder\file.zip)   |
| Путь         | String                           | Путь к файлам архива (c:\folder)                  |
| Формат       | LTools.Data.Model.ArchiveFormats | Формат архива                                     |
| Пароль       | String                           | Пароль архива                                     |
| Путь к 7-zip | String                           | Путь к 7zip.dll (C:\Program Files\7-Zip\7z.dll)   |

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
