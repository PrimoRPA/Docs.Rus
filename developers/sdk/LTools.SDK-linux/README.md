# Создание элемента для Studio (Linux)

В этом разделе вы узнаете, как разработать элемент для Primo RPA Studio на Linux. Чтобы создать элемент, вам понадобится интегрированная среда разработки Visual Studio (IDE). 

Вам будет легче, если вы уже разрабатывали элементы для Primo RPA Studio на Windows, поскольку процесс отличается незначительно.


## Начало работы

Создайте проект в Visual Studio:

1. Запустите Visual Studio и выберите **Создание проекта** (Create a new project).
2. Выберите шаблон проекта **Библиотека классов** (Class Library) и нажмите **Далее**.

   ![](<../../../.gitbook/assets1/template's-project.png>)
   
3. В названии проекта обязательно укажите префикс **Primo.**. Пример: `Primo.My.Elements`.
4. Далее выберите фреймворк **.NET 6.0** и нажмите **Создать**.

   ![](<../../../.gitbook/assets1/framework.png>)

5. В меню Visual Studio выберите **Проект > Добавить ссылку на проект...**. В открывшемся окне нажмите кнопку **Обзор...** и откройте каталог установки Primo RPA Studio под Linux. Добавьте из него в свой проект следующие файлы:
   * LTools.Common.dll
   * LTools.Dto.dll
   * LTools.Enums.dll
   * LTools.Scripting.dll
   * LTools.SDK.dll
   * Primo.UIControls.dll
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
4. Localization — файлы локализации при необходимости.

> \*Вы можете использовать другие папки и названия в своем проекте.


## Создание элемента
Для создания элемента Primo вам понадобится:
1. Создать визуальную часть элемента — файл \*.axaml. 
2. Создать программную часть элемента — файл \*.cs.
3. Связать две части элемента.
4. Собрать проект в библиотеку `Primo.*.dll`.
5. Упаковать библиотеку в NuGet-пакет и опубликовать на портале [NuGet](www.nuget.org). 



### Шаг 1. Создаем визуальную часть элемента Primo

1. Вызовите контекстное меню папки Views, выберите **Добавить > Создать элемент > User Control (Avalonia)**.
2. В поле **Имя** укажите его название, например, `MyFirstActivity_Form.axaml`.
3. Нажмите кнопку **Добавить**.

Готово — вы создали компонент, который является визуальной составляющей элемента Primo. Данные будущего элемента автоматически будут смаплены на DataContext данного контролла.


#### Работа с файлом *.axaml.cs

При создании файла \*.axaml также автоматически добавится файл *.axaml.cs. Откройте в рабочей области файл `*.axaml.cs`, измените в нем класс с **UserControl** на **PrimoUserControl** из `clrnamespace:LTools.Common.UIElements;assembly=LTools.Common`. Пример:

```
using Avalonia.Controls;
using LTools.Common.UIElements;

namespace Primo.SDK.Sample.Views
{
    public partial class MyFirstActivity_Form : PrimoUserControl
    {
        public MyFirstActivity_Form()
        {
            if (LTools.Common.Helpers.WFHelper.DoRender)
                InitializeComponent();
        }
    }
}
```

#### Работа с файлом *.axaml

Откройте в рабочей области ваш файл `*.axaml`. Смените в нем класс с **UserControl** на **PrimoUserControl** из `clrnamespace:LTools.Common.UIElements;assembly=LTools.Common`. 

Пример:

```
<ui:PrimoUserControl xmlns="https://github.com/avaloniaui"
 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
 xmlns:ui="clr-namespace:LTools.Common.UIElements;assembly=LTools.Common">


</ui:PrimoUserControl>
```

Теперь спроектируйте визуальный облик элемента Primo. Подумайте, какие вы хотите увидеть на панели элемента поля, кнопки и т.д. 

![](<../../../.gitbook/assets1/RenderActivity.png>)


В соответствии с вашим дизайном создайте сетку (Grid). Пример:

```
<ui:PrimoUserControl xmlns="https://github.com/avaloniaui"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
             xmlns:ui="clr-namespace:LTools.Common.UIElements;assembly=LTools.Common"
             mc:Ignorable="d" d:DesignWidth="800" d:DesignHeight="450"
             x:Class="Primo.SDK.Sample.Views.TestComponentSimpleBase">

  <Grid>
    <Label Content="Test"/>
  </Grid>

</ui:PrimoUserControl>
```

Форма в Visual Studio может не отображаться из-за ошибки "No Executable" - данная ошибка связана с Avalonia. 



### Шаг 2. Создаем программную часть элемента Primo

Вызовите контекстное меню папки Elements, выберите **Добавить > Создать элемент > Класс C#**.  Укажите имя класса, например, `MyFirstActivity.cs`. Данный класс будет содержать программную часть (code-behind) элемента Primo, описывать его логику.

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


### Шаг 3. Связываем две части элемента Primo

Для изменения значения свойства Prop1 в визуальной части элемента, нужно использовать Binding.

Пример:
```
<ui:PrimoUserControl xmlns="https://github.com/avaloniaui"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
             xmlns:ui="clr-namespace:LTools.Common.UIElements;assembly=LTools.Common"
             mc:Ignorable="d" d:DesignWidth="800" d:DesignHeight="450"
             x:Class="Primo.SDK.Sample.Views.TestComponentSimpleBase">
 <Grid>
   <TextBox Content="Test" Text="{Binding Prop1}"/>
 </Grid>

</ui:PrimoUserControl>
```

### Шаг 4. Собираем проект 

В панели **Solution Explorer** (Обозреватель решений) вызовите контекстное меню решения и выберите **Собрать решение**. В результате сборки будет получена библиотека `Primo.*.dll`.

Данную библиотеку можно скопировать в каталог установки Primo Studio. Если библиотека не содержит ошибок, то после запуска Студии элементы из вашей библиотеки появятся на панели «Элементы». 

О том, как отладить элемент библиотеки, вы можете узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/debugging).


### Шаг 5. Упаковываем библиотеку в NuGet-пакет и публикуем

Аналогично инструкции для SDK под Windows. Подробнее см. [здесь](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/publish).



## Дополнительно

В нашем публичном репозитории на [GitHub](https://github.com/PrimoRPA/SDK.Sample) вы можете найти каталог **LTools.SDK-for-Linux**, в котором представлен демонстрационный проект **Primo.SDK.Avalonia.Sample**. Вы можете скачать его и открыть в своей Visual Studio для просмотра.













