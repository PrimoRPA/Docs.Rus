# Приложение Excel

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (253).png>)

![](<../../../.gitbook/assets/image (412).png>)

Компонент производит подключение к приложению Excel. 

Особенности работы с файлами определяются драйвером, выбранным в соответствующем свойстве:
1. DX - работает с файлом без Microsoft Office, вследствие чего имеет более высокую производительность. Хорошо подходит для небольших файлов, поддерживается на всех указанных ОС. Недостатки: не работает с макросами и, если файл большой, может занимать много памяти. 
2. Interop - работает с файлом через запуск приложения. Поддерживает макросы, не занимает много оперативной памяти. Недостатки: работает медленнее, чем DX, не поддерживается на OS Linux. 

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство         | Тип                               | Описание                                                                             |
| ---------------- | --------------------------------- | ------------------------------------------------------------------------------------ |
| Драйвер          | LTools.Office.Model. InteropTypes | Тип драйвера подключения: DX или Interop |
| R1C1             | Boolean                           | Только для DX. Установка флага позволяет задавать диапазон, используя стиль ссылок [R1C1](https://learn.microsoft.com/ru-ru/office/troubleshoot/excel/numeric-columns-and-rows#a1-reference-style-vs-r1c1-reference-style). По умолчанию флаг снят, диапазоны указываются в формате A1 
| Путь к файлу     | String                            | Путь к файлу документа Excel (C:\folder\file.xlsx)                                   |
| Проверять файл   | Boolean                           | При установке флага будет выполняться проверка на наличие файла. Если проверка выявит, что файл Excel отсутствует, то: 1) При записи новой информации робот создаст файл Excel и добавит в него данные. 2) При попытке чтения несуществующего файла вернется ошибка
| Массив байтов    | byte\[]                           | Массив байтов документа                                                              |
| Разделитель      | String                            | Разделитель колонок. Для режима Interop необходима кодировка UTF-8 BOM или UTF-16 LE |
| Отображать Excel | Boolean                           | Отображать приложение Excel на экране (только для Interop)                           |


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, System.IO.File.ReadAllBytes("file"), ";", LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app = LTools.Office.ExcelApp.Init(wf, System.IO.File.ReadAllBytes("file"), ";", LTools.Office.Model.InteropTypes.DX)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var app = _lib.LTools.Office.ExcelApp.Init(wf, _lib.System.IO.File.ReadAllBytes("file"), ";", _lib.LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}
{% endtabs %}
