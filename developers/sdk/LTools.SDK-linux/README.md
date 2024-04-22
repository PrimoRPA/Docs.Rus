# Создание элемента для Studio (Linux)

В этом разделе вы узнаете, как разработать элемент для Primo RPA Studio на Linux. Чтобы создать элемент, вам понадобится интегрированная среда разработки Visual Studio (IDE). 

Вам будет легче, если вы уже разрабатывали элементы для Primo RPA Studio на Windows, поскольку процесс отличается незначительно.


## Начало работы

Создайте проект в Visual Studio:

1. Запустите Visual Studio и выберите **Создание проекта** (Create a new project).
2. Выберите шаблон проекта **Библиотека классов** (Class Library) и нажмите **Далее**.

   ![](<../../../.gitbook/assets1/template's-project.png>)
   
3. В названии проекта обязательно укажите префикс **Primo.**. Пример: `Primo.Test`.
4. Далее выберите фреймворк **.NET 6.0** и нажмите **Создать**.

   ![](<../../../.gitbook/assets1/framework.png>)

5. В меню Visual Studio выберите **Проект > Добавить ссылку на проект...**. В открывшемся окне нажмите кнопку **Обзор...** и откройте каталог установки Primo RPA Studio под Linux. Добавьте из него в свой проект следующие файлы:
   * LTools.Common.dll
   * LTools.Dto.dll
   * LTools.Enums.dll
   * LTools.Scripting.dll
   * LTools.SDK.dll
   * Primo.UIControls.dll

   ![](<../../../.gitbook/assets1/add-refs-2.png>)

6. Перейдите в панель инструментов **Обозреватель решений** (Solution Explorer), вызовите контекстное меню проекта и выберите **Управление пакетами NuGet**. Установите следующие сборки:
   * Avalonia 0.10.18
   * Avalonia.Desktop 0.10.18
   * Avalonia.Diagnostics 0.10.18
   * Avalonia.Xaml.Behaviors 0.10.18
   * MessageBox.Avalonia 2.1.0
   * XamlNameReferenceGenerator 1.5.1

   ![](<../../../.gitbook/assets1/add-nugets.png>)

7. Установите расширение Avalonia for Visual Studio. Для этого выберите раздел меню **Расширения > Управление расширениями** и введите в поисковой строке `Avalonia` для выдачи нужных результатов.


## Структура проекта 

Для удобства работы с проектом создайте в нем папки\*:
1. Elements — файлы с описанием логики элементов.
2. Views — визуальные формы элементов.
3. Images — иконки элементов. Формат png, размер 24x24.
4. Localization — файлы ресурсов при необходимости.

Пример:

![](<../../../.gitbook/assets1/sdk-project-folders.png>)

> \*Вы можете использовать другие папки и названия в своем проекте.


## Создание элемента
Для создания элемента Primo вам понадобится:
1. Создать визуальную часть элемента — файл \*.axaml. 
2. Создать программную часть элемента — файл \*.cs.
3. Связать две части элемента.
4. Собрать проект в библиотеку `Primo.*.dll`.
5. Упаковать библиотеку в NuGet-пакет и опубликовать на портале [NuGet](www.nuget.org). 

Впоследствии вы можете установить ваш NuGet-пакет в Primo RPA Studio на Linux, чтобы добавить элемент в среду RPA-разработки.


### Шаг 1. Создаем визуальную часть элемента Primo

1. Вызовите контекстное меню папки Views, выберите **Добавить > Создать элемент > User Control (Avalonia)**.
2. В поле **Имя** укажите его название. Пример: `WriteInConsoleBase.axaml`.
3. Нажмите кнопку **Добавить**.

Готово — вы создали компонент, который является визуальной составляющей элемента Primo. Данные будущего элемента автоматически будут смаплены на DataContext данного контролла.


#### Работа с файлом *.axaml.cs

При создании файла \*.axaml также автоматически добавится файл *.axaml.cs. Откройте в рабочей области файл `*.axaml.cs`, измените в нем класс с **UserControl** на **PrimoUserControl** из `clrnamespace:LTools.Common.UIElements;assembly=LTools.Common`. 

Например, мы открыли файл `WriteInConsoleBase.axaml.cs` и изменили в нем класс:

```
using Avalonia.Interactivity;
using LTools.Common.UIElements;

namespace Primo.TestNuget.Views
{
    public partial class WriteInConsoleBase : PrimoUserControl
    {
        /// <summary>
        /// Constructor.
        /// </summary>
        public WriteInConsoleBase()
        {
            if (LTools.Common.Helpers.WFHelper.DoRender)
            {
                InitializeComponent();
            }
        }

        /// <summary>
        /// Event "OnClick" on element "Form_btn" handling method.
        /// </summary>
        /// <param name="sender">Sender value.</param>
        /// <param name="eventArguments">Event arguments value.</param>
        private void Form_btn_OnClick(object? sender, RoutedEventArgs eventArguments)
        {
            this.Form_txt.Text = @"""'Ваше имя', 'Ваша фамилия'""";
        }
    }
}
```

#### Работа с файлом *.axaml

Откройте в рабочей области ваш файл `*.axaml`. Смените в нем класс с **UserControl** на **PrimoUserControl** из `clrnamespace:LTools.Common.UIElements;assembly=LTools.Common`. 

Например, мы открыли файл `WriteInConsoleBase.axaml` и изменили в нем класс:

```
uiElements:PrimoUserControl xmlns="https://github.com/avaloniaui"
                     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                     xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                     xmlns:uiElements="clr-namespace:LTools.Common.UIElements;assembly=LTools.Common"
                     xmlns:uiControls="clr-namespace:Primo.UIControls;assembly=Primo.UIControls"
                     mc:Ignorable="d" d:DesignWidth="800" d:DesignHeight="450"
                     x:Class="Primo.TestNuget.Views.WriteInConsoleBase">

...

</ui:PrimoUserControl>
```

Теперь спроектируйте визуальный облик элемента Primo. Подумайте, какие вы хотите увидеть на панели элемента поля, кнопки и т.д. 

![](<../../../.gitbook/assets1/RenderActivity.png>)


В соответствии с вашим дизайном создайте сетку (Grid). Например, мы хотим создать простой элемент с полем для ввода данных и кнопкой «Установить шаблон»:

```
<uiElements:PrimoUserControl xmlns="https://github.com/avaloniaui"
                     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                     xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                     xmlns:uiElements="clr-namespace:LTools.Common.UIElements;assembly=LTools.Common"
                     xmlns:uiControls="clr-namespace:Primo.UIControls;assembly=Primo.UIControls"
                     mc:Ignorable="d" d:DesignWidth="800" d:DesignHeight="450"
                     x:Class="Primo.TestNuget.Views.WriteInConsoleBase">
    <Grid RowDefinitions="*,*" ColumnDefinitions="*">
        <uiControls:PrimoTextBox x:Name="Form_txt"  Grid.Row="0" Text="{Binding Text}" />
        <Button x:Name="Form_btn" Grid.Row="1" Content="{Binding ButtonContent}" Click="Form_btn_OnClick"/>
    </Grid>
</uiElements:PrimoUserControl>
```

:small_blue_diamond: *Форма в Visual Studio может не отображаться из-за ошибки "No Executable" - данная ошибка связана с Avalonia.*

![](<../../../.gitbook/assets1/No Executable1.png>)

Пример созданной панели элемента Primo:

![](<../../../.gitbook/assets1/sdk-панелька.png>)



### Шаг 2. Создаем программную часть элемента Primo

Вызовите контекстное меню папки Elements, выберите **Добавить > Создать элемент > Класс C#**.  Укажите имя класса, например, `WriteInConsole.cs`. Данный класс будет содержать программную часть (code-behind) элемента Primo, описывать его логику.

Для создания элемента:
* с синхронным поведением необходимо унаследовать класс `LTools.SDK.PrimoComponentSimple<UI>`.
* с тайм-аутом необходим класс `LTools.SDK.PrimoComponentTO<UI>`.

Где `<UI>` – это имя визуальной части элемента Primo.

Дополнительно о том, как создать:
* [Синхронный элемент](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/sync-element).
* [Элемент с тайм-аутом](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/to-element).
* [Простой контейнер](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/simple-container).
* [Специальный контейнер](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/custom-container).
* [Расширенные свойства элемента](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/extended-properties).
* [Дополнительные методы](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/additional-methods).
* [Кастомные свойства](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/custom-properties).
* [Валидация ввода](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/input-validation).

Например, мы создаем синхронный элемент Primo:

```
using System.ComponentModel;
using Avalonia.Controls;
using LTools.Common.Helpers;
using LTools.Common.Model;
using LTools.Common.UIElements;
using LTools.SDK;
using Primo.TestNuget.Views;
using Primo.UIControls;

using WriteInConsoleStrings = Primo.TestNuget.Properties.WriteInConsole;

namespace Primo.TestNuget.Elements;

/// <summary>
/// Element "WriteInConsole" model class.
/// </summary>
public class WriteInConsole : PrimoComponentSimple<WriteInConsoleBase>
{
    #region BackingFields

    /// <summary>
    /// Text for console writing field.
    /// </summary>
    private string _text = string.Empty;

    /// <summary>
    /// Button content field.
    /// </summary>
    private string _buttonContent = WriteInConsoleStrings.BUTTON_CONTENT;

    /// <summary>
    /// Element group name field.
    /// </summary>
    private string _groupName = WriteInConsoleStrings.GROUP_NAME;

    /// <summary>
    /// Properties panel field.
    /// </summary>
    private static PrimoPropertyGrid _properties;

    #endregion

    #region Properties

    /// <summary>
    /// Properties panel property.
    /// </summary>
    public override Control Properties
    {
        get
        {
            _properties = WFHelper.ProduceProperties(_properties, this);

            _properties.PropertyDefinitions.Add(WFHelper.ProduceScriptEditorProperty("Text", _properties, WriteInConsoleStrings.PROPERTY_TEXT_TOOLTIP));

            return _properties;
        }
    }

    /// <summary>
    /// Text for console writing property.
    /// </summary>
    [LTools.Common.Model.Serialization.StoringProperty]
    [LTools.Common.Model.Studio.ValidateReturnScript(DataType = typeof(string))]
    [LocalizedCategory("PROPERTY_GROUP", typeof(WriteInConsoleStrings)), LocalizedDisplayName("PROPERTY_TEXT_NAME", typeof(WriteInConsoleStrings)), DefaultValue(0)]
    public string Text
    {
        get => this._text;

        set
        {
            this._text = value;

            this.InvokePropertyChanged(this, "Text");
        }
    }

    /// <summary>
    /// Button content property.
    /// </summary>
    public string ButtonContent
    {
        get => this._buttonContent;
        set => this._buttonContent = value;
    }

    /// <summary>
    /// Element group name property.
    /// </summary>
    public override string GroupName
    {
        get => this._groupName;
        protected set => _groupName = value;
    }

    #endregion

    /// <summary>
    /// Constructor.
    /// </summary>
    /// <param name="container">Base element container value.</param>
    public WriteInConsole(IWFContainer container) : base(container)
    {
        sdkComponentIcon = "avares://Primo.TestNuget/Images/WriteInConsoleIcon.png";
        sdkComponentName = WriteInConsoleStrings.DEFAULT_NAME;
        sdkComponentHelp = WriteInConsoleStrings.HELP_TEXT + "\n" + WriteInConsoleStrings.PROPERTY_TEXT_NAME + ": " + WriteInConsoleStrings.PROPERTY_TEXT_TOOLTIP;

        this.InitClass(container);
    }

    /// <summary>
    /// Execution element method.
    /// </summary>
    /// <param name="sd">Scripting data value.</param>
    /// <returns>Element execution result value.</returns>
    public override ExecutionResult SimpleAction(ScriptingData sd)
    {
        try
        {
            var messsage = $"Привет {Text}.{Environment.NewLine}Вы создали свой первый элемент в Primo SDK!";

            Console.WriteLine(messsage);

            return new ExecutionResult
            {
                SuccessMessage = string.Format(WriteInConsoleStrings.MSG_INFO_SUCCESS, messsage),
                IsSuccess = true
            };
        }
        catch (Exception exception)
        {
            return new ExecutionResult
            {
                ErrorMessage = exception.Message,
                IsSuccess = false
            };

        }
    }
}
```


### Шаг 3. Связываем две части элемента Primo

Привяжите данные к UI. Для изменения значения вашего свойства в визуальной части элемента используйте Binding.

Пример для нашего элемента **WriteInConsoleBase**:

```
<uiElements:PrimoUserControl xmlns="https://github.com/avaloniaui"
                     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                     xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                     xmlns:uiElements="clr-namespace:LTools.Common.UIElements;assembly=LTools.Common"
                     xmlns:uiControls="clr-namespace:Primo.UIControls;assembly=Primo.UIControls"
                     mc:Ignorable="d" d:DesignWidth="800" d:DesignHeight="450"
                     x:Class="Primo.TestNuget.Views.WriteInConsoleBase">

    <Grid RowDefinitions="*,*" ColumnDefinitions="*">
        <uiControls:PrimoTextBox x:Name="Form_txt"  Grid.Row="0" Text="{Binding Text}" />
        <Button x:Name="Form_btn" Grid.Row="1" Content="{Binding ButtonContent}" Click="Form_btn_OnClick"/>
    </Grid>

</uiElements:PrimoUserControl>
```


### Шаг 4. Собираем проект 

В панели **Обозреватель решений** вызовите контекстное меню решения и выберите **Собрать решение**. В результате сборки будет получена библиотека `Primo.<Название вашей библиотеки>.dll`.

О том, как отладить элемент библиотеки, вы можете узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/debugging).


### Шаг 5. Упаковываем библиотеку в NuGet-пакет и публикуем

Аналогично инструкции для SDK под Windows. Подробнее см. [здесь](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/publish).

Опубликованный NuGet-пакет вы можете затем установить в свою Студию на Линукс при помощи Менеджера зависимостей:

![](<../../../.gitbook/assets1/sdk-setup-nuget.png>)

Элементы из вашей библиотеки появятся на панели «Элементы». Например, наш элемент отобразился так:

![](<../../../.gitbook/assets1/sdk-элементы.png>)

Он обладает следующими свойствами:

![](<../../../.gitbook/assets1/sdk-свойства.png>)



## Дополнительно

В нашем публичном репозитории на [GitHub](https://github.com/PrimoRPA/SDK.Sample) вы можете найти каталог **LTools.SDK-for-Linux**, в котором представлен демонстрационный проект **Primo.SDK.Avalonia.Sample**. Вы можете скачать его и открыть в своей Visual Studio для просмотра.













