# Таблица ODF

![](<../../../../.gitbook/assets1/Cropped-ODFtable.png>)

Компонент, производящий подключение к приложению Excel. Компонент служит контейнером для других элементов, работающих с Excel.
В случае отсутствия указанного файла будет создан новый.

**Важно:** чтобы сохранить изменения в Excel-файле, используйте в конце работы элемент **Сохранить документ**.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Путь к файлу** *[String]*: Путь к файлу документа Excel. Пример: `C:\folder\file.xlsx`.
2. **Проверять файл**: Проверка на наличие указанного файла Excel. 
3. **Пароль** *[String]*: Пароль от файла Excel.
4. **Пароль (зашифрованный)** *[[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-8.0)]*: Зашифрованный пароль от файла Excel. 
5. **Массив байтов** *[byte\[]]*: Массив байтов документа.

## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, "file");
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, System.IO.File.ReadAllBytes("file"));
```
{% endtab %}

{% tab title="Python" %}
```python
app = Primo.Office.OdfOxml.ExcelApp.Init(wf, "file")
app = Primo.Office.OdfOxml.ExcelApp.Init(wf, System.IO.File.ReadAllBytes("file"))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.Primo.Office.OdfOxml.ExcelApp.Init(wf, "file");
var app = _lib.Primo.Office.OdfOxml.ExcelApp.Init(wf, _lib.System.IO.File.ReadAllBytes("file"));
```
{% endtab %}
{% endtabs %}
