# Таблица ODF

Элемент устанавливает подключение к приложению, работающему с таблицами ODF. Путь до файла с таблицей указывается в свойствах элемента. Если данный файл отсутствует, будет создан новый.

Элемент «Таблица ODF» также выступает контейнером по отношению к другим компонентам, обрабатывающим указанный файл.

![Контейнер «Таблица ODF»](<../../../../.gitbook/assets1/windows_items/odf-attach-table-app.png>)


## Свойства
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Путь к файлу** *[String]* — путь к файлу с ODF-таблицей.
2. **Проверять файл** — определяет, нужно ли использовать проверку на наличие указанного файла. По умолчанию проверка не используется.
3. **Пароль** *[String]* — пароль от файла при наличии.
4. **Пароль (зашифрованный)** *[[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0)]* — защищенный пароль от файла. 
5. **Массив байтов** *[byte\[]]* — массив байтов документа.


## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, "file");
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, System.IO.File.ReadAllBytes("file"));
```
{% endtab %}
{% endtabs %}

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
