# Расширенные свойства элемента

1. **Имя элемента** — задается в свойстве `sdkComponentName` в конструкторе до вызова метода InitClass. Имя элемента отображается в палитре «Элементы».

2. **Текст помощи** — задается в свойстве `sdkComponentHelp` в конструкторе до вызова метода InitClass. Текст помощи отображается в нижней части палитры свойств элемента.

3. **Иконка элемента** — задается в свойстве `sdkComponentIcon` в конструкторе до вызова метода InitClass. Путь к иконке выполняется в стандартном для WPF-приложений формате. 

   Пример: `“pack://application:,,/Primo.SDKSample;component/Images/sample.png”`, где:
   * **Primo.SDKSample** – имя библиотеки;
   * **Images** – имя папки, содержащей рисунок;
   * **sample.png** – имя файла рисунка. 
 
   :small_orange_diamond: **Внимание!** Не забудьте пометить **Build Action** файла рисунка как **Resource**.

4. **Ссылка на ресурс помощи** — URL сайта онлайн-справки по элементу задается в свойстве `sdkComponentHelpUrl`. Ссылка на портал Primo находится в константе `WFElementBase.HELP_URL_ROOT`.

    Пример:

```csharp
public PrimoElementBack(IWFContainer container) : base(container)
{
    sdkComponentName = "My sync element";
    sdkComponentHelp = "This is my first sync element";
    sdkComponentIcon = "pack://application:,,/Primo.SDKSample;component/Images/sample.png";
    sdkComponentHelpUrl = "http://...";
    InitClass(container);
}

```
