# Извлечь архив

![](<../../../../.gitbook/assets/image (44).png>)

Компонент, распаковывающий архив файлов.

| Свойство       | Тип    | Описание                                              |
| -------------- | ------ | ----------------------------------------------------- |
| Архив          | String | Путь к распаковываемому архиву (c:\folder\file.zip)   |
| Путь           | String | Путь к папке извлечения (c:\folder)                   |
| Пароль         | String | Пароль архива                                         |
| Путь к 7-zip\* | String | Путь к 7zip.dll (C:\Program Files\7-Zip\7z.dll)       |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Data.ArchiveApp.Extract(wf, "Путь разархивации", "Архив", "Пароль", "Genm r 7-zip");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Data.ArchiveApp.Extract(wf, "Путь разархивации", "Архив", "Пароль", "Genm r 7-zip")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Data.ArchiveApp.Extract(wf, "Путь разархивации", "Архив", "Пароль", "Genm r 7-zip");
```
{% endtab %}
{% endtabs %}
