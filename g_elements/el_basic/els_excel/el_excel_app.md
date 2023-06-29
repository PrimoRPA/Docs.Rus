# Приложение Excel

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1).png>)

![](<../../../.gitbook/assets/image (412).png>)

Компонент производит подключение к приложению Excel.

Особенности работы с файлами определяются драйвером, выбранным в соответствующем свойстве:

1. DX - работает с файлом без Microsoft Office, вследствие чего имеет более высокую производительность. Хорошо подходит для небольших файлов, поддерживается на всех указанных ОС. Недостатки: не работает с макросами и, если файл большой, может занимать много памяти.
2. Interop - работает с файлом через запуск приложения. Поддерживает макросы, не занимает много оперативной памяти. Недостатки: работает медленнее, чем DX, не поддерживается на Linux.

**ВАЖНО!** При необходимости сохранять изменения в файле Excel используйте в конце работы элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/el_excel_save).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство         | Тип                               | Описание                                                                                |
| ---------------- | --------------------------------- | --------------------------------------------------------------------------------------- |
| ***Excel***      |          |       |
| Драйвер          | LTools.Office.Model.InteropTypes  | Тип драйвера подключения: DX или Interop                                                |
| R1C1             | Boolean                           | Только для DX. Установка флага позволяет задавать диапазон, используя стиль ссылок [R1C1](https://learn.microsoft.com/ru-ru/office/troubleshoot/excel/numeric-columns-and-rows#a1-reference-style-vs-r1c1-reference-style). По умолчанию флаг снят, диапазоны указываются в формате A1 |
| Путь к файлу     | String                            | Путь к файлу документа Excel (C:\folder\file.xlsx)          |
| Присоединяться   | Boolean                           | Только для Interop. При установке флага возможно присоединиться к открытому вручную файлу. **Важно!** Если вы присоединились к такому файлу, закрывать его тоже потребуется вручную |
| Загружать AddIn-ы | Boolean                          | Только для Interop. Определяет, нужно ли загружать установленные дополнения. Подробнее о надстройках Excel можно узнать [здесь](https://learn.microsoft.com/ru-ru/office/dev/add-ins/excel/excel-add-ins-overview) |
| Отображать Excel | Boolean                           | Только для Interop. Если параметр включен, на экране будет отображаться приложение Excel |
| Проверять файл   | Boolean                           | При установке флага будет выполняться проверка на наличие файла. Если проверка выявит, что файл Excel отсутствует, то: 1) При записи новой информации робот создаст файл Excel и добавит в него данные. 2) При попытке чтения несуществующего файла вернется ошибка |
| Массив байтов    | byte\[]                           | Массив байтов документа                                     |
| ***Csv***  |   |   |
| Разделитель      | String                            | Разделитель колонок. Для режима Interop необходима кодировка UTF-8 BOM или UTF-16 LE |


## Загрузка надстроек
Для загрузки надстроек, используемых в Excel, существует специальное свойство **Загружать AddIn-ы** (Interop) - при его включении будет совершена попытка загрузить все активные надстройки разом. Но бывают случаи, когда использование этого свойства не помогает загрузить нужную надстройку. Например, если для нее нужны права администратора\*, или если есть конфликт с центром безопасности MS Office. 

\**Например, для установки/удаления надстроек COM нужны права администратора. Свойство **Загружать AddIn-ы** не сможет их установить.* 

Если запуск Робота с правами администратора не приводит к загрузке надстроек, то, вероятно, происходит вмешательство центра безопасности MS Office. Например, источник файла (файла надстройки?) расценивается им как неблагоприятный. В этом случае следует [правильным образом сконфигурировать MS Office](https://support.microsoft.com/ru-ru/office/%D0%B2%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B8-%D0%BE%D1%82%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BF%D0%B0%D1%80%D0%B0%D0%BC%D0%B5%D1%82%D1%80%D0%BE%D0%B2-%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-activex-%D0%B2-%D1%84%D0%B0%D0%B9%D0%BB%D0%B0%D1%85-office-f1303e08-a3f8-41c5-a17e-b0b8898743ed#:~:text=%D0%9E%D1%82%D0%BA%D1%80%D0%BE%D0%B9%D1%82%D0%B5%20%D0%B2%D0%BA%D0%BB%D0%B0%D0%B4%D0%BA%D1%83%20%D0%A4%D0%B0%D0%B9%D0%BB.%2c%D0%A4%D0%B0%D0%B9%D0%BB%20%D1%81%D1%82%D0%B0%D0%BD%D0%B5%D1%82%20%D0%BD%D0%B0%D0%B4%D0%B5%D0%B6%D0%BD%D1%8B%D0%BC%20%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%BC): необходимо, чтобы при вызове приложения по ярлыку (Пуск > Программы > Excel) оно загружало требуемые надстройки без ограничений от центра безопасности. Тогда и Еxcel, запущенный через контейнер **Приложение Excel** (Interop), загрузит нужные надстройки.

Запуск Excel из [командной строки](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_prog/el_prog_cmd) обычным образом не загружает все надстройки, поэтому меню и функциональность могут отличаться. Чтобы этого не происходило, команда запуска должна включать дополнительный ключ `/x`:

> *"/x Starts a new instance (a separate process) of Excel."*

Пример\**:
```
"excel.exe /x "c:\My Folder\book1.xlsx""
```
Если к командной строке добавить этот переключатель, то вид Еxcel, запущенный из командной строки, будет соответствовать внешнему виду приложения, запущенному через контейнер **Приложение Excel** (Interop).
Подробнее про особенности командной строки можно прочитать [здесь](https://support.microsoft.com/en-us/office/command-line-switches-for-microsoft-office-products-079164cd-4ef5-4178-b235-441737deb3a6).

\*\**Вся команда в элементе **Командная строка** должна быть в кавычках.*

## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

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
