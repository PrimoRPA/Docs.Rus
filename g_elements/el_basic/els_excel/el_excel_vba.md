---
description: Invoke VBA
---

# Запустить VBA

Элемент выполняет скрипт VBA в файле Excel. Работает только с драйвером **Interop**. 

Драйвер и другие базовые настройки указываются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). Если в файле Excel требуется сохранить изменения, используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![](<../../../.gitbook/assets/image (577).png>)

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство    | Тип           | Описание                     |
| ----------- | ------------- | ---------------------------- |
| **Excel:** |              |                              |
| Файл\*      | String        | Путь к файлу скрипта         |
| Функция\*   | String        | Имя функции VBA              |
| Аргументы\* | List\<object> | Аргументы скрипта. Максимальное количество - 20 аргументов |
| Видимость\* | Boolean       | Видимость Excel              |
| Асинхронный | Boolean       | Признак асинхронного выполнения |
| Тайм-аут    | int           | Тайм-аут исполнения макроса (мс) |
| **Вывод:** |              |                              |
| Переменная  | Object        | Переменная, которая будет хранить результат выполнения скрипта |

## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//vbaFile - Файл VBA: [String] Путь к файлу с VBA кодом 
//vbaFunction - Функция VBA: [String] Имя вызываемой функции VBA
//vbaArguments - Аргументы VBA: [List<Object>] Список аргументов VBA
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, System.IO.Path.GetFullPath(".\\TestData.xlsx"), ";", LTools.Office.Model.InteropTypes.Interop);
String vbaFile = System.IO.Path.GetFullPath(".\\vba.bas");
String vbaFunction = "WriteToCell";
List<Object> vbaArguments = new List<Object>(){"A11","Лист1","Text from Primo"};
app.RunVBA(vbaFile,vbaFunction,vbaArguments,true);
app.Save();
app.App.Dispose();
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#name - Файл: [String] Путь к файлу скрипта
#func - Функция: [String] Имя функции VBA
#args - Аргументы: [List<object>] Аргументы скрипта
#visible - Видимость: Видимость Excel

app = LTools.Office.ExcelApp.Init(wf, System.IO.Path.GetFullPath(".\\TestData.xlsx"),";", LTools.Office.Model.InteropTypes.Interop)
	
vbaFile = System.IO.Path.GetFullPath(".\\addTextToCell.bas")
vbaFunction = "AddTextToCells"
vbaArguments = None

data = app.RunVBA(vbaFile, vbaFunction, vbaArguments, True) #Object
app.Save()
app.App.Dispose()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//name - Файл: [String] Путь к файлу скрипта
//func - Функция: [String] Имя функции VBA
//args - Аргументы: [List<object>] Аргументы скрипта
//visible - Видимость: Видимость Excel

//Необходимо указывать абсолютный путь до файла Excel и до VBA скрипта
let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.Interop);

var vbaFile = ".\\addTextToCell.bas";
var vbaFunction = "AddTextToCells";
var vbaArguments = null;

var data = app.RunVBA(vbaFile, vbaFunction, vbaArguments ,  true); //Object
app.Save();
app.App.Dispose();
```
{% endtab %}
{% endtabs %}
