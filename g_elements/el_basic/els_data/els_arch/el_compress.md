# Создать архив

*Eng: Create Archive*

 Элемент для создания архива файлов. Используется, когда нужно сжать набор файлов для передачи или хранения.

 ![](<../../../../.gitbook/assets/image (340).png>)

### Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
Символ `@` в значениях свойств позволяет не экранировать обратные слеши.

| Свойство     | Тип                              | Описание                                          |
| ------------ | -------------------------------- | ------------------------------------------------- |
| ***Архивирование*** | | | 
| Архив\*      | String                          | Cтроковое значение, которое указывает путь к создаваемому архиву. Например, `@"C:\folder\file.zip"`|
| Путь\*       | String                          | Cтроковое значение, которое указывает путь к файлам, которые нужно архивировать. Например, `@"C:\folder\"`       |
| Формат\*     | LTools.Data.Model.ArchiveFormats | Формат архива: по умолчанию установлен `Zip`. Чтобы выбрать другое значение, откройте выпадающий список |
| Пароль       | String                           | Cтроковое значение, которое представляет собой пароль архива, если он есть                                 |
|7-zip path*   | String     | Cтроковое значение, которое указывает путь к 7zip.dll. Например, `C:\Program Files\7-Zip\7z.dll`



###  Learning

Для изучения работы с элементом **Создать архив**, вы можете скачать обучающий RPA-проект по следующей ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip)

1. Скачайте архив с обучающими материалами с указанной страницы.
2. Распакуйте архив и откройте проект `StudioActivities` в вашей среде разработки.
3. Найдите процесс `StudioActivities/Ru/Данные/Архивирование.ltw` для изучения работы элемента.


## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

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
