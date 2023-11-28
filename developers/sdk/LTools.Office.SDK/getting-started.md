# Начало работы

1. Запустите Visual Studio.
2. Выберите **Create a new project** с типом проекта Class Library (.NET Framework).
3. Введите имя проекта. **ВНИМАНИЕ!** **Имя проекта и библиотеки dll должны начинаться с префикса "Primo."** 
4. Выберите фреймворк .NET Framework 4.6.1.
5. Найдите в папке Primo Studio указанные ниже сборки и добавьте их в References проекта сборки:
   * _LTools.Common.dll_
   * _LTools.Dto.dll_
   * _LTools.Enums.dll_
   * _LTools.Scripting.dll_
   * _LTools.SDK.dll_
   * _LTools.Office.dll_
 
   Найдите сборки MS Office в Assemblies > Extensions менеджера зависимостей Visual Studio.\
   Для работы с **Excel** добавьте:
   * _DevExpress.Docs.v20.1.dll_
   * _DevExpress.Spreadsheet.v20.1.Core.dll_
   * _DevExpress.Office.v20.1.Core.dll_
   * _Microsoft.Office.Interop.Excel (необходим установленный MS Office)_

   Для работы с **Word** добавьте:
   * _DevExpress.Docs.v20.1.dll_
   * _DevExpress.RichEdit.v20.1.Core.dll_
   * _DevExpress.Office.v20.1.Core.dll_
   * _Microsoft.Office.Interop.Word (необходим установленный MS Office)_

   Для работы с **Outlook** добавьте:
   * _Microsoft.Office.Interop.Outlook (необходим установленный MS Office)_
   
   Для работы с **Exchange** добавьте:
   * _Microsoft.Exchange.WebServices.dll_

   Также добавьте стандартные сборки:

   * _PresentationCore_
   * _PresentationFramework_
   * _System.Xaml_
   * _WindowsBase_

   ![](<../../../.gitbook/assets1/sdk-office-start.png>)

6\. Добавьте в проект компонент типа **User Control (WPF)** (Add > New Item...)

   ![](<../../../.gitbook/assets/1 (118).png>)

   Данный элемент будет являться визуальной составляющей нашего элемента Primo. Данные будущего элемента автоматически будут смаплены на DataContext этого контролла (пример приводится далее).

7\. Создайте класс (Add > Class…). Этот класс будет являться code-behind нашего элемента.

8\. Для создания элемента с синхронным поведением необходимо унаследовать класс `LTools.Office.SDK.PrimoComponent*<UI>`, где:
* UI – это имя вашего визуального компонента из шага 5.
* Вместо `*` нужно выбрать Excel, Word, Outlook либо Exchange, в зависимости от целевого использования. Пример: LTools.Office.SDK.PrimoComponentExcel.

Дальше все из стандартного SDK относится и к этому, поскольку LTools.Office.SDK его наследует.

