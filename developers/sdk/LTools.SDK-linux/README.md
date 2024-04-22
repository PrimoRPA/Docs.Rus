# Создание элемента для Studio (Linux)

В этом разделе вы узнаете, как разработать элемент для Primo RPA Studio на Linux. Чтобы создать элемент, вам понадобится интегрированная среда разработки Visual Studio (IDE). 

Вам будет легче, если вы уже разрабатывали элементы для Primo RPA Studio на Windows, поскольку процесс отличается незначительно.


## Начало работы

> В нашем примере мы использовали Visual Studio Community 2022.

Создайте проект в Visual Studio:

1. Запустите Visual Studio и выберите **Create a new project** (Создание проекта).
2. Выберите шаблон проекта **Class Library** (Библиотека классов).
3. В открывшейся форме:
   * Обязательно укажите в названии проекта префикс **Primo.** Пример: `Primo.My.Activity`.
   * Выберите фреймворк **.NET 6.0.**.
4. Выберите раздел меню **Проект > Добавить ссылку на проект...**. В открывшемся окне нажмите кнопку **Обзор...** и откройте каталог установки Primo RPA Studio (Linux). Вам нужно добавить из него в свой проект следующие файлы:
   * LTools.Common.dll
   * LTools.Dto.dll
   * LTools.Enums.dll
   * LTools.Scripting.dll
   * LTools.SDK.dll
   * Primo.UIControls.dll
   * Primo.UIControls.dll
5. Установите для проекта Nuget-пакеты. Для этого перейдите в панель инструментов **Solution Explorer** (Обозреватель решений), вызовите контекстное меню проекта и выберите **Управление пакетами NuGet**. Установите следующие сборки:
   * Avalonia 0.10.18
   * Avalonia.Desktop 0.10.18
   * Avalonia.Diagnostics 0.10.18
   * Avalonia.Xaml.Behaviors 0.10.18
   * MessageBox.Avalonia 2.1.0
   * XamlNameReferenceGenerator 1.5.1
6. Установите расширение Avalonia for Visual Studio 2022. Для этого выберите раздел меню **Extentions > Manage Extentions** (Расширения > Управление расширениями) и введите в поисковой строке `Avalonia`.


## Структура проекта 

Для удобства работы с проектом создайте в нем следующие папки\*:
1. Classes — классы, которые будут использоваться в элементах в рамках вашей библиотеки.
2. Elements — элементы, которые войдут в вашу библиотеку.
3. Images — иконки будущих элементов.  - //только иконки или еще что-то? Какие форматы изображений разрешены (только png?)? Есть ли рекомендуемые размеры и ограничения?
4. Localization — файлы локализации.
5. Views — визуальные формы элементов.

![](.gitbook/assets1/)

> \*Вы можете использовать другие названия для ваших папок.


## Проектирование элемента
Для создания элемента Primo вам понадобится:
1. Создать визуальную часть элемента.
2. Создать программную часть элемента. 
3. Связать две части элемента.
4. Собрать проект в библиотеку `Primo.*.dll`.
5. Упаковать библиотеку в NuGet-пакет и опубликовать на портале [NuGet](www.nuget.org). 




## Шаг 1 — Создаем визуальную часть элемента

> фактически то же самое, что и в винде

1. Вызовите контекстное меню папки Elements, выберите **Добавить > Создать элемент > Класс C# Class**.  Укажите имя класса, например, `MyFirstActivity.cs`.
2. Вызовите контекстное меню папки Views, выберите **Добавить > Создать элемент > User Control (Avalonia)**. Укажите его имя, например, `MyFirstActivity_Form.axaml`.

Откройте в рабочей области файл `MyFirstActivity_Form.axaml`. Давайте отобразим сетку. Создайте 2 колонки и 3 строки.  

Let's display the grid -> Grid property -> ShowGridLines="True"

Just replace new Grid this code:  (Просто замените новый Grid на этот код:)

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

Итак, у нас определены столбцы и строки. Под строкой `</Grid.RowDefinitions>` добавьте изображение: 
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

Далее второй столбец первой строки, где будет название нашего элемента:
Next the second column of the first row, where we will have the name of our activity:

```
<Grid rid.Row="0" Grid.Column="1">
    <!-- Activity Name -->
    <Label Content="My First Activity"/>
</Grid>
```

Далее перейдем ко второй строке первого столбца. Сетка пустая.
Next First Column and Second Row. Grid is Empty

```
<Grid Grid.Row="1" Grid.Column="0">
  <!-- Row 1 -->
</Grid>
```

И наконец, во втором столбце второй строки добавим сетку и кнопку к ней.
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

НЕТУ Написать, что форма визуально не отрисовывается в вижуал студии и ошибка No Executable - это нормально. Уточнить у Адреянова, мож, как-то можно настроить.

And First Build! -> Solution Explorer -> Right Click "Solution 'Primo.My.Activity'" -> Clean Solution -> Build Solution.


Check in output 1 Successed!


And Result:

ПИКЧА С ГОТОВОЙ ФОРМОЙ (В АВАЛОНИИ ПОХОДУ НЕ СДЕЛАЕМ)




## Шаг 2 — Создаем программную часть элемента 

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


## Шаг 3 — Связываем две части элемента 




## Шаг 4 — Собираем проект 


**Как настроить название проекта (или правильнее - пакета?)**   ///и зачем это делать

В окне Solution Explorer разверните Properties проекта и дважды щелкните файл `AssemblyInfo.cs`. Затем заполните поля, как на рисунке ниже:

(Рисунок Алексея)

___________________

В панели **Solution Explorer** (Обозреватель решений) вызовите контекстное меню решения и выберите **Собрать решение**. В результате сборки будет получена библиотека `Primo.*.dll`.

Данную библиотеку можно скопировать в каталог установки Primo Studio. Если библиотека не содержит ошибок, то после запуска Студии элементы из вашей библиотеки появятся на панели «Элементы». 

О том, как отладить созданный элемент, вы можете узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/debugging).


## Шаг 4 — Упаковываем библиотеку в NuGet-пакет и публикуем

Аналогично инструкции для SDK под Windows. Подробнее см. [здесь](https://docs.primo-rpa.ru/primo-rpa/developers/ltools.sdk/publish).

















