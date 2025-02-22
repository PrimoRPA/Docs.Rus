---
description: Excel workbook
---

# Приложение Excel

Контейнер, который производит подключение к приложению Microsoft Excel и открывает указанный файл. Настройки подключения и путь до файла указываются в свойствах контейнера. 

Вы можете добавлять в контейнер **Приложение Excel** другие элементы из группы Excel для работы с открытым файлом. В конце работы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/prilozhenie-excel/el\_excel\_save), чтобы все изменения в файле применились.

![Контейнер «Приложение Excel»](<../../../.gitbook/assets1/excel-workbook-1.png>)


## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

#### Excel:

1. **Драйвер** *[LTools.Office.Model.InteropTypes]* — тип драйвера подключения: DX или Interop. Драйвер определяет особенности работы с файлом. По умолчанию используется DX.\
   \
   Сравнительная таблица драйверов
   
   | Характеристика        | DX (DevExpress)                                               |  Interop                                                  |
   | --------------------  | ------------------------------------------------------------- | --------------------------------------------------------  |
   | Тип подключения       | Работает с файлом без Microsoft Office. Это означает, что Microsoft Excel на компьютере робота может отсутствовать | Работает с файлом через запуск приложения Microsoft Excel |
   | ОС                    | Windows, Linux, MacOS                                         | Только Windows |
   | Поддерживает макросы и скрипты VBA  |  Нет                                            | Да |
   | Скорость работы       |  Выше                                                         | Ниже |
   

1. **Путь к файлу** *[String]* — путь к файлу документа Excel. Пример: `@"C:\folder\file.xlsx"`. Символ @ используется для экранирования обратного слеша.
1. **Пароль** *[String]* — пароль для открытия [защищенного](https://support.microsoft.com/ru-ru/office/%D0%B7%D0%B0%D1%89%D0%B8%D1%82%D0%B0-%D1%84%D0%B0%D0%B9%D0%BB%D0%B0-excel-7359d4ae-7213-4ac2-b058-f75e9311b599) файла Excel.
1. **Пароль (зашифрованный)** *[[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0)]* — зашифрованный пароль от файла. В целях безопасности пароль в формате SecureString не хранится в открытом виде. Получить его можно, например, из программы «Диспетчер учетных данных» (Credential Manager), после чего вставить в это поле.
1. **Проверять файл** *[Boolean]* — определяет, нужно ли проверять наличие указанного файла Excel. Возможные значения:
   * *чекбокс установлен* — если проверка обнаружит, что указанного файла не существует, робот завершит работу с ошибкой;
   * *чекбокс снят* — робот выполнит работу без ошибок, даже если файла не существует. При попытке записать информацию в несуществующий файл, будет создан файл Excel с указанным именем. В конце работы этот файл потребуется [сохранить](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/prilozhenie-excel/el\_excel\_save).
1. **Массив байтов** *[byte\[]]* — массив байтов документа. Если указан массив, то свойство «Путь к файлу» заполнять не нужно. Свойство работает с обоими драйверами.
1. **Присоединяться** *[Boolean]* — только для Interop. Установка чекбокса позволяет присоединиться к файлу, который открыт вручную. Закрывать такой файл тоже придется вручную.
1. **Открывать только на чтение** *[Boolean]* — только для Interop. Определяет, нужно ли открывать указанный файл только для чтения. По умолчанию чекбокс не установлен. Настройка будет проигнорирована в следующих случаях:
   * если включено свойство «Присоединяться»;
   * если указан массив байтов;
   * если используется файл в формате текста с разделителями.
1. **Загружать AddIn-ы** *[Boolean]* — только для Interop. Определяет, нужно ли переподключать установленные дополнения (надстройки). Общие сведения о надстройках Excel приведены [здесь](https://learn.microsoft.com/ru-ru/office/dev/add-ins/excel/excel-add-ins-overview). Подробнее о работе этого свойства см. ниже, в подразделе [Надстройки Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app#id-2.-nadstroiki-excel).
1. **Отображать Excel** *[Boolean]* — только для Interop. Если параметр включен, на экране будет отображаться приложение Excel.
1. **R1C1** *[Boolean]* — только для DX. Установка чекбокса позволяет указывать диапазон ячеек в элементах Excel, используя стиль ссылок [R1C1](https://learn.microsoft.com/ru-ru/office/troubleshoot/excel/numeric-columns-and-rows#a1-reference-style-vs-r1c1-reference-style). По умолчанию чекбокс выключен, а диапазоны указываются в формате A1. При использовании стиля R1C1, убедитесь, что он также установлен в файле Excel — подробнее см. в подразделе [Стиль ссылок R1C1](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app#id-1.-stil-ssylok-r1c1).
1. **Сохранить изменения** *[Boolean]* — По умолчанию чекбок неактивен, что позволяет избежать случайного сохранения изменений. При активации чекбокса внесенные изменения будут сохранены автоматически. ***Функция доступна с версии 1.24.10***


#### Csv:

* **Разделитель** *[String]* — разделитель колонок в файле с расширением \*.csv. По умолчанию `";"`. Для режима Interop необходима кодировка UTF-8 BOM или UTF-16 LE.


## Дополнительно

### 1. Стиль ссылок R1C1

Excel может использовать стиль ссылок R1C1, в котором строки и столбцы представлены в виде чисел на рабочем листе. Стиль ссылок R1C1 полезен для вычисления позиций строк и столбцов в макросах. В стиле R1C1 Excel указывает расположение ячейки с "R", за которой следует номер строки, и "C", за которой следует номер столбца.

Чтобы установить/снять в Excel стиль R1C1, выполните действия:

1. Запустите Microsoft Excel.
2. В меню **Файл** щелкните пункт **Параметры**.
3. Откройте вкладку **Формулы**.
4. В разделе **Работа с формулами** щелкните, чтобы установить/снять чекбокс **Стиль ссылок R1C1**, затем нажмите кнопку **ОК**.

При установке чекбокса **Стиль ссылок R1C1** будет изменен стиль ссылок заголовков строк и столбцов, а ссылки на ячейки из стиля A1 изменятся на стиль R1C1.

### 2. Надстройки Excel

Чтобы воспользоваться установленными надстройками в Excel, их требуется перезагрузить. За это в контейнере отвечает свойство **Загружать AddIn-ы**: с его помощью будет совершена попытка переподключить все активные надстройки. Список активных надстроек можно просмотреть в Excel в меню **Файл > Параметры > Надстройки**.

Однако бывают случаи, когда использование свойства не помогает загрузить какую-то надстройку. Например, если для нее нужны права администратора, или если есть конфликт с центром безопасности MS Office. В этом случае воспользуйтесь рекомендациями ниже, в зависимости от выбранного способа запуска приложения.

{% hint style="info" %}
Например, права администратора нужны для установки/удаления надстроек COM. Свойство **Загружать AddIn-ы** не сможет их установить.
{% endhint %}


#### 2.1. Запуск по ярлыку 

Если запуск робота не приводит к перезагрузке надстроек, то, вероятно, происходит вмешательство центра безопасности MS Office. Например, источник файла расценивается как неблагоприятный. В этом случае следует [правильным образом сконфигурировать MS Office](https://support.microsoft.com/ru-ru/office/%D0%B2%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B8-%D0%BE%D1%82%D0%BA%D0%BB%D1%8E%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BF%D0%B0%D1%80%D0%B0%D0%BC%D0%B5%D1%82%D1%80%D0%BE%D0%B2-%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-activex-%D0%B2-%D1%84%D0%B0%D0%B9%D0%BB%D0%B0%D1%85-office-f1303e08-a3f8-41c5-a17e-b0b8898743ed): необходимо, чтобы при вызове приложения по ярлыку (Пуск > Программы > Excel) оно загружало требуемые надстройки без ограничений от центра безопасности. Тогда Еxcel, запущенный через контейнер **Приложение Excel**, тоже загрузит нужные надстройки.

#### 2.2. Запуск из командной строки

Запуск Excel из [командной строки](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_prog/el\_prog\_cmd) обычным образом не загружает все надстройки, поэтому меню и функциональность приложения могут отличаться. Чтобы этого не происходило, команда запуска должна содержать дополнительный ключ `/x`:

> _"/x Starts a new instance (a separate process) of Excel."_

Пример:

```
"excel.exe /x "c:\My Folder\book1.xlsx""
```

Если к командной строке добавить этот переключатель, то вид Еxcel, запущенный из командной строки, будет соответствовать внешнему виду приложения, запущенному через контейнер **Приложение Excel** (Interop). Подробнее про особенности командной строки можно прочитать [здесь](https://support.microsoft.com/en-us/office/command-line-switches-for-microsoft-office-products-079164cd-4ef5-4178-b235-441737deb3a6).

{% hint style="info" %}
Вся команда в элементе **Командная строка** должна быть в кавычках.
{% endhint %}


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
