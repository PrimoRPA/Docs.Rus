# Расширенные свойства

**Имя элемента**. За имя элемента отвечает свойство sdkComponentName, задаваемое в конструкторе до вызова метода InitClass. Имя элемента отображается в палитре *Элементы*.

**Текст помощи**. Текст помощи задается свойством sdkComponentHelp в конструкторе до вызова метода InitClass. Помощь отображается в нижней части палитры свойств элемента.

**Иконка**. Иконка элемента задается при помощи свойства sdkComponentIcon в конструкторе до вызова метода InitClass. Путь к иконке выполняется в стандартном для WPF-приложений формате. 

Пример: `“pack://application:,,/Primo.SDKSample;component/Images/sample.png”`, где:
* **Primo.SDKSample** – имя библиотеки;
* **Images** – имя папки, содержащей рисунок;
* **sample.png** – имя файла рисунка. 
 
:small_red_triangle: **ВНИМАНИЕ!** Не забудьте пометить **Build Action** файла рисунка как **Resource**.

**Ссылка на ресурс помощи.** URL сайта онлайн-справки по элементу задается с помощью свойства sdkComponentHelpUrl. Ссылка на портал Primo находится в константе WFElementBase.HELP\_URL\_ROOT.

Например:

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
