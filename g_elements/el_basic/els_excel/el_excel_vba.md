# Запустить VBA

![](<../../../.gitbook/assets/image (577).png>)

Элемент выполняет указанный скрипт VBA в файле Excel. 

:bangbang: ***Работает только с драйвером Interop.***

Примечания:

1. Путь до файла Excel, тип драйвера и прочие параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). Внутрь этого контейнера помещается элемент **Запустить VBA**.
2. Если в документе Excel требуется сохранить изменения, то после всех действий с файлом используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство    | Тип           | Описание                     |
| ----------- | ------------- | ---------------------------- |
| ***Excel:*** |              |                              |
| Файл\*      | String        | Путь к файлу скрипта         |
| Функция\*   | String        | Имя функции VBA              |
| Аргументы\* | List\<object> | Аргументы скрипта. Максимальное количество - 20 аргументов |
| Видимость\* | Boolean       | Видимость Excel              |
| Асинхронный | Boolean       | Признак асинхронного выполнения |
| Тайм-аут    | int           | Тайм-аут исполнения макроса (мс) |
| ***Вывод:*** |              |                              |
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
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, System.IO.Path.GetFullPath(".\\searching.xlsx"), ";", LTools.Office.Model.InteropTypes.Interop);
String vbaFile = System.IO.Path.GetFullPath(".\\vba.bas");
String vbaFunction = "WriteToCell";
List<Object> vbaArguments = new List<Object>(){"A11","Лист1","Text from Primo"};
app.RunVBA(vbaFile,vbaFunction,vbaArguments,true);
app.Save();
app.App.Dispose();
```
{% endtab %}
