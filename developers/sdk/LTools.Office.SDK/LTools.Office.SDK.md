# Дополнительные свойства

## Свойство GroupName

**GroupName** - необязательное свойство. Позволяет сгруппировать элементы по категориям. Если не переопределить **GroupName**, элементы попадут в соответствующие группы панели элементов.

Названия групп можно получить из:

-	LTools.Office.ExcelInst.ELEMENTS_GROUP_NAME
-	LTools.Office.WordInst.ELEMENTS_GROUP_NAME
-	LTools.Office.OutlookInst.ELEMENTS_GROUP_NAME
-	LTools.Office.OfficeInst.InteropExchange.ELEMENTS_GROUP_NAME

Пример:

```csharp
using LTools.Common.Model;
using LTools.Common.UIElements;
using LTools.SDK;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Primo.SDKSample
{
    public class PrimoElementBack : LTools.Office.SDK.PrimoComponentExcel<WFSampleExcelBase>
    {
        public override string GroupName 
        { 
            get => LTools.Office.ExcelInst.ELEMENTS_GROUP_NAME; 
            protected set { }
        }

        public PrimoElementBack(IWFContainer container) : base(container)
        {
            InitClass(container);
        }

        public override ExecutionResult SimpleAction(ScriptingData sd)
        {
            return new ExecutionResult();
        }
    }
}
```


## Свойство Driver

Каждый класс **LTools.Office.SDK.PrimoComponent\*** обладает свойством **Driver**, которое обеспечивает взаимодействие с приложениями MS Office. В свойстве содержится информация о типе автоматизации и ссылки на объекты, связанные с конкретным приложением.

Свойство **Driver** может иметь один из следующих типов:

-   LTools.Office.SDK.ExcelDriver
-	LTools.Office.SDK.WordDriver
-	LTools.Office.SDK.OutlookDriver
-	LTools.Office.SDK.ExchangeDriver


Например, тип **.ExcelDriver** содержит ссылку на объект `LTools.Office.ExcelInst`, который представляет собой оболочку для работы с Excel. Также этот тип содержит ссылку на книгу Excel для DX (DevExpress.Spreadsheet.Workbook) и ссылку на приложение Excel для Interop (Microsoft.Office.Interop.Excel.Application).

Аналогично, тип **.WordDriver** содержит ссылку на объект `LTools.Office.WordInst`. 

Тип **.OutlookDriver** содержит ссылку на объект `LTools.Office.OutlookInst`, а тип **.ExchangeDriver** - на объект `LTools.Office.OfficeInst.InteropExchange`.

### Функциональность

Объекты, связанные с конкретным приложением MS Office, предоставляют доступ к функциональности этих приложений.

Например, с помощью объекта `LTools.Office.ExcelInst` можно выполнять операции с ячейками и диапазонами в Excel, создавать, открывать и сохранять книги.

Объект `LTools.Office.WordInst` позволяет работать с документами Word, включая создание, открытие и сохранение документов, а также форматирование текста и добавление изображений.

Объект `LTools.Office.OutlookInst` предоставляет возможность отправлять и получать электронные письма, управлять папками и элементами почты в Outlook.

Объект `LTools.Office.OfficeInst.InteropExchange` позволяет работать с Exchange Server, включая отправку и получение электронных писем, управление календарями и контактами.


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

