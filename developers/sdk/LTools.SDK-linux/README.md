# Создание элемента для Studio (Linux)

В этом разделе вы узнаете, как разработать элемент для Primo RPA Studio на Linux. Готовый элемент необходимо будет упаковать в dll-библиотеку и затем установить в вашу Primo RPA Studio. 

Чтобы создать элемент, вам понадобится интегрированная среда разработки Visual Studio (IDE). 


## Начало работы

> В нашем примере мы использовали Visual Studio Community 2022.

Создайте проект в Visual Studio:

1. Запустите Visual Studio и выберите **Create a new project** (Создание проекта).
2. Выберите шаблон проекта **Class Library (.NET Framework)** - \\\\для линукса нужен такой же шаблон?
3. В открывшейся форме:
   * Укажите имя проекта. Оно должно начинаться с префикса **Primo.** Пример: `Primo.My.Activity`. - \\\\нужна ли галка "Поместить проект и решение в одном каталоге" при создании проекта?
   * Выберите фреймворк **.NET Framework 4.6.1**. - /// актуально для линукс?
6. Откройте окно инструментов **Solution Explorer** (Обозреватель решений). Добавьте в **References** (Ссылки) вашего проекта следующие файлы из каталога установки Primo RPA Studio (Linux):
   * LTools.Common.dll
   * LTools.Dto.dll - нужно или нет для линукс?
   * LTools.Enums.dll
   * LTools.Scripting.dll
   * LTools.SDK.dll
7. Также добавьте в ваш проект стандартные сборки: ////- нужны ли они для Линукса? У Алексея в инструкции они не указаны.
   * PresentationCore;
   * PresentationFramework;
   * System.Xaml;
   * WindowsBase.


:small_blue_diamond: **Вопрос**: у Алексея в инструкции написано: "File Class1.cs needs to be deleted!".  Что это за файл, откуда берется и зачем удалять.


### Установка Avalonia

1. Выберите в Visual Studio пункт меню **Extentions > Manage Extentions** (Расширения > Управление расширениями).
3. Введите в поисковой строке `Avalonia`, чтобы найти расширения, которые понадобятся для проекта.
4. Установите следующие расширения (чтобы они установились, понадобится потом закрыть все окна Visual Studio):
   * Avalonia for Visual Studio 2022;
   * Avalonia Toolkit;
   * Avalonia Templates Studio.
5. В окне инструментов Solution Explorer вызовите контекстное меню проекта и выберите Manage Nuget Package (Управление пакетами NuGet). Установите следующие библиотеки: - \\\"короче там в Dependencies нужно установить библиотеки". Dependencies руками создаем? или можно установить в References? туда автоматом устанавливает
   * Avalonia by Avalonia;
   * Avalonia Desktop;
   * Avalonia Diagnostics;
   * Avalonia ReactiveUI;
   * XamlNameReferenceGenerator.

Они понадобятся при написании кода.

## Структура проекта 

Для удобства работы с проектом создайте в нем следующие папки\*:
1. Classes — классы, которые будут использоваться в элементах в рамках вашей библиотеки.
2. Elements — элементы, которые войдут в вашу библиотеку.
3. Images — иконки будущих элементов.  - //только иконки или еще что-то? Какие форматы изображений разрешены (только png?)? Есть ли рекомендуемые размеры и ограничения?
4. Localization — файлы локализации.
5. Views — визуальные формы элементов.

![](.gitbook/assets1/)

> \*Вы можете использовать другие названия для ваших папок.


///Вопрос: это более-менее общая структура для всех библиотек? что из этих папок обязательно, а что опционально? Что еще может быть в проекте?
Название (Primo.Somethig.Linux) - проекта в студии у лехи


## Проектирование элемента
Для создания элемента вам понадобится:
1. Создать визуальную форму элемента:
   * Спроектировать визуальную форму.
   * Написать код для визуальной формы.
2. Описать логику работы вашего элемента. 
3. Привязать визуальную форму к коду логики элемента.
4. Билд и публикация.




## Шаг 1 — Создаем визуальную форму элемента

> фактически то же самое, что и в винде

1. Вызовите контекстное меню папки Elements, выберите **Добавить > Создать элемент > Класс C# Class**.  Укажите имя класса, например, `MyFirstActivity.cs`.
2. Вызовите контекстное меню папки Views, выберите **Добавить > Создать элемент > User Control (Avalonia)**. Укажите его имя, например, `MyFirstActivity_Form.axaml`.

Откройте в рабочей области файл `MyFirstActivity_Form.axaml`. Создайте 2 колонки и 3 строки.  Let's display the grid -> Grid property -> ShowGridLines="True"

Just replace new Grid this code:

```
<Grid x:Name="MyFirstActivity_Form_grd" 
            VerticalAlignment="Center" 
            HorizontalAlignment="Center" 
            ShowGridLines="True"
            Background="White"
            
  >
    <Grid.ColumnDefinitions>
        <ColumnDefinition></ColumnDefinition>
        <ColumnDefinition></ColumnDefinition>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition></RowDefinition>
        <RowDefinition></RowDefinition>
    </Grid.RowDefinitions>
  </Grid>
```

Okay, Column Definitions and Row Definitions Exists, then under </Grid.RowDefinitions> add a picture:

```
<Grid Grid.Row="0" Grid.Column="0">
<!--Мы создали сетку для for the first column of the first row (для первой строки первого столбца? или наоборот?) и хотим вставить сюда изображение.-->
  <Image HorizontalAlignment="Left" 
         Source="pack://application:,,/Primo.My.Activity;component/Images/logo.png"
         <!--Путь к изображению. Состоит из названия библиотеки (Primo.My.Activity) и пути внутри библиотеки (Images/logo.png")-->
         Height="40"
         Width="40"
         <!--Размер изображения-->
         Margin="5,5,5,5"
         <!--Отступ от границ сетки: слева, сверху, справа, снизу.-->
  />
</Grid>
```


Далее второй столбец первой строки, где будет название нашей деятельности:
Next the second column of the first row, where we will have the name of our activity:

```
<Grid rid.Row="0" Grid.Column="1">
    <!-- Activity Name -->
    <Label Content="My First Activity"/>
</Grid>
```


Next First Column and Second Row. Grid is Empty

```
<Grid Grid.Row="1" Grid.Column="0">
  <!-- Row 1 -->
</Grid>
```

And at the end, in the second column of the second row, we will add a grid and a button to it:
```
<Grid  Grid.Row="1" Grid.Column="1">
  <Button x:Name="Form_btn" Content="Open" />
</Grid>
```


И полная сетка:
```
<Grid x:Name="MyFirstActivity_Form_grd" 
      VerticalAlignment="Center" 
      HorizontalAlignment="Center" 
      ShowGridLines="True"
      Background="White"
>
    <Grid.ColumnDefinitions>
        <ColumnDefinition></ColumnDefinition>
        <ColumnDefinition></ColumnDefinition>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition></RowDefinition>
        <RowDefinition></RowDefinition>
    </Grid.RowDefinitions>
    <Grid Grid.Row="0" Grid.Column="0">
        <Image HorizontalAlignment="Left" 
             Source="pack://application:,,/Primo.My.Activity;component/Images/eye_logo.png"
             Height="40"
             Width="40"
             Margin="5,5,5,5"
        />
    </Grid>
    <Grid Grid.Row="0" Grid.Column="1">
        <!-- Activity Name -->
        <Label Content="My First Activity"/>
    </Grid>
    <Grid Grid.Row="1" Grid.Column="0">
        <!-- Row 1 -->
    </Grid>
    <Grid  Grid.Row="1" Grid.Column="1">
        <Button x:Name="Form_btn" Content="Open" />
    </Grid>
</Grid>
```

Отрисовка в Visual Studio:

НЕТУ

And First Build! -> Solution Explorer -> Right Click "Solution 'Primo.My.Activity'" -> Clean Solution -> Build Solution.


Check in output 1 Successed!


And Result:

ПИКЧА С ГОТОВОЙ ФОРМОЙ (В АВАЛОНИИ ПОХОДУ НЕ СДЕЛАЕМ)




## Шаг 2 — Описываем логику работы элемента 








## Шаг 3 — Привязываем форму к логике работы элемента 




## Шаг 4 — Билд и упаковка в нугет-пакет

Click Bulding
If Building is success, then go to Folder of Project
Open Primo.My.Activity\bin\Debug
Looking for a file Primo.My.Activity.dll and copy to Desktop
Open Nuget Package Explorer
Add lib Folder
Add to lib file Primo.My.Activity.dll and eye_nuget.png(from Images)
Fill in the fields
Save Nuget
Upload To Studio
And Use



You are welcome! :-)






## Как что-то создать

**Как добавить в проект визуальную составляющую элемента:**

Добавьте в проект компонент типа **User Control (WPF)** (Add ➝ New Item…). Данный элемент будет являться визуальной составляющей нашего элемента Primo. Данные будущего элемента автоматически будут смаплены на DataContext данного контролла (пример будет приведен далее).

(сама форма не отображается в вижуал студио -> по-моему, намеренно, поискать в чатах "защита от воровства")

Леха просто скопировал вьюшку из виндового проекта. 

Написать, что форма визуально не отрисовывается в вижуал студии и ошибка No Executable - это нормально. Уточнить у Адреянова, мож, как-то можно настроить.


**Как создать класс элемента:**

Создайте класс (Add ➝ Class…). Данный класс будет являться code-behind нашего элемента.

Для создания элемента:
* с синхронным поведением необходимо унаследовать класс LTools.SDK.PrimoComponentSimple<UI>.
* с тайм-аутом необходим класс LTools.SDK.PrimoComponentTO<UI>.

Где UI – это имя вашего визуального компонента из шага 5.


(написать определения, что такое синхронный элемент, а что такое элемент с таймаутом)



**Как загрузить в проект изображения:**

Правой кнопкой мыши кликните по папке Images, выберите Add > Existing Item... и загрузите нужные изображения. 

Затем кликните правой кнопкой мыши каждое изображение и откройте Properties. В группе свойств Advanced выберите для Buld Action значение Resource. (зачем это делать? это всегда и для всех картинок нужно делать? или только для иконок элемента?)


**Как настроить название проекта (или правильнее - пакета?)**   ///и зачем это делать

В окне Solution Explorer разверните Properties проекта и дважды щелкните файл `AssemblyInfo.cs`. Затем заполните поля, как на рисунке ниже:

(Рисунок Алексея)


## Создание элемента

Правой кнопкой мыши кликните по папке Elements и выберите Add -> New Item... -> Choose C# Class. Укажите имя элемента, например, `MyFirstActivity.cs` и нажмите Add.


### Визуальный облик элемента

(фактически то же самое, что и в винде. Леша копипастил)

Далее правой кнопкой мыши кликните по папке Views и выберите Add -> New Item... -> выберите User Control (WPF) -> Name: MyFirstActivity_Form.xaml -> Add.

<здесь у Алексея рисунки от руки с дизайном элемента>

Дважды кликните по файлу `MyFirstActivity_Form.xaml` и создайте колонки и строки (для чего?). В нашем примере мы создадим 2 колонки и 2 строки (но может быть и больше?). После чего отобразите получившуюся (сетку) - откройте Grid property -> ShowGridLines="True"

Просто замените новый Grid на этот код:

```
  <Grid x:Name="MyFirstActivity_Form_grd" 
            VerticalAlignment="Center" 
            HorizontalAlignment="Center" 
            ShowGridLines="True"
            Background="White"
            
  >
    <Grid.ColumnDefinitions>
        <ColumnDefinition></ColumnDefinition>
        <ColumnDefinition></ColumnDefinition>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition></RowDefinition>
        <RowDefinition></RowDefinition>
    </Grid.RowDefinitions>
  </Grid>
```

Итак, у нас определены столбцы и строки. Затем под строкой `</Grid.RowDefinitions>` добавьте изображение: 

