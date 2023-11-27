# LTools.Office.SDK

LTools.Office.SDK - это набор инструментов и компонентов, предоставляющих доступ к функциональности таких приложений Microsoft Office, как Excel, Word, Outlook и Exchange.

## Свойство GroupName

GroupName - необязательное свойство. Оно позволяет группировать элементы по категориям палитры элементов. Например, можно установить значение "Форматирование" для свойства GroupName, чтобы все элементы палитры, относящиеся к форматированию, отображались в одной группе.

В случае, если свойство GroupName не переопределено, элементы попадут в соответствующие группы палитры элементов.

Названия групп можно получить из:

-	LTools.Office.ExcelInst.ELEMENTS_GROUP_NAME
-	LTools.Office.WordInst.ELEMENTS_GROUP_NAME
-	LTools.Office.OutlookInst.ELEMENTS_GROUP_NAME
-	LTools.Office.OfficeInst.InteropExchange.ELEMENTS_GROUP_NAME


## Классы PrimoComponent

Классы **PrimoComponent** представляют собой компоненты, которые предоставляют доступ к функциональности различных приложений Microsoft Office.

У каждого компонента есть свойство **Driver**, которое содержит информацию о типе автоматизации (DX/Interop) и ссылки на объекты, связанные с конкретным приложением.

-	LTools.Office.SDK.ExcelDriver
-	LTools.Office.SDK.WordDriver
-	LTools.Office.SDK.OutlookDriver
-	LTools.Office.SDK.ExchangeDriver


Например, свойство **Driver** типа **ExcelDriver** содержит ссылку на объект LTools.Office.ExcelInst, который представляет собой оболочку для работы с Excel. Также свойство Driver содержит ссылку на книгу Excel для DX (DevExpress.Spreadsheet.Workbook) и ссылку на приложение Excel для Interop (Microsoft.Office.Interop.Excel.Application).

Аналогично, свойство **Driver** типа **WordDriver** содержит ссылку на объект LTools.Office.WordInst, свойство Driver типа OutlookDriver содержит ссылку на объект LTools.Office.OutlookInst, а свойство Driver типа ExchangeDriver содержит ссылку на объект LTools.Office.OfficeInst.InteropExchange.

## Функциональность

Объекты, связанные с конкретным приложением, предоставляют доступ к функциональности соответствующих приложений Microsoft Office.

Например, с помощью **LTools.Office.ExcelInst** можно выполнять операции с ячейками и диапазонами в Excel, создавать, открывать и сохранять книги.

**LTools.Office.WordInst** позволяет работать с документами Word, включая создание, открытие и сохранение документов, а также форматирование текста и добавление изображений.

**LTools.Office.OutlookInst** предоставляет возможность отправлять и получать электронные письма, управлять папками и элементами почты в Outlook.

**LTools.Office.OfficeInst.InteropExchange** позволяет работать с Exchange Server, включая отправку и получение электронных писем, управление календарями и контактами.


## ExcelDriver

| Название | Тип | Описание | Ссылка |
| --- | --- | --- | --- |
| Excel | LTools.Office.ExcelInst | Ссылка на оболочку Excel | - |
| InteropType | LTools.Office.Model.InteropTypes | Тип автоматизации (DX/Interop) | - |
| DXExcelApp | DevExpress.Spreadsheet.Workbook | Ссылка на книгу Excel (для DX) | [DevExpress](https://docs.devexpress.com/OfficeFileAPI/DevExpress.Spreadsheet.Workbook?v=20.1) |
| InteropExcelApp | Microsoft.Office.Interop.Excel.Application | Ссылка на приложение Excel (для Interop) | [Microsoft](https://learn.microsoft.com/en-us/dotnet/api/microsoft.office.interop.excel.application) |

## WordDriver

| Название | Тип | Описание | Ссылка |
| --- | --- | --- | --- |
| Word | LTools.Office.WordInst | Ссылка на оболочку Word | - |
| InteropType | LTools.Office.Model.InteropTypes | Тип автоматизации (DX/Interop) | - |
| DXCurrentDoc | DevExpress.XtraRichEdit.API.Native.Document | Ссылка на документ Word (для DX) | [DevExpress](https://docs.devexpress.com/OfficeFileAPI/DevExpress.XtraRichEdit.API.Native.Document?v=20.1) |
| InteropWordApp | Microsoft.Office.Interop.Word.Application | Ссылка на приложение Word (для Interop) | [Microsoft](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.office.interop.word.application) |

## OutlookDriver

| Название | Тип | Описание | Ссылка |
| --- | --- | --- | --- |
| Outlook | LTools.Office.OutlookInst | Ссылка на оболочку Outlook | - |
| InteropOutlookApp | Microsoft.Office.Interop.Outlook.Application | Ссылка на приложение Outlook | [Microsoft](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.office.interop.outlook.application) |

## ExchangeDriver

| Название | Тип | Описание | Ссылка |
| --- | --- | --- | --- |
| Exchange | LTools.Office.OfficeInst.InteropExchange | Ссылка на оболочку Exchange | - |
| InteropExchangeApp | Microsoft.Exchange.WebServices.Data.ExchangeService | Ссылка на приложение Exchange | [Microsoft](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.exchange.webservices.data.exchangeservice) |

