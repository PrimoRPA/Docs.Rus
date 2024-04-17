# Создание библиотеки для Studio (Linux)

Раздел посвящен разработке собственных элементов для использования в Primo RPA Studio на Linux. Элементы поставляются в Studio в виде dll-библиотеки. 

Чтобы создать такую библиотеку, вам понадобится среда разработки Visual Studio (IDE). Установите ее на компьютер.


**Вопросы**. Может быть, что-нибудь еще нужно? (какая-нибудь авелония) Предъявляются ли требования к версии Visual Studio?



## Начало работы
Сначала создадим проект в Visual Studio:

1. Запустите Visual Studio.
2. Выберите **Create a new project** с шаблоном проекта **Class Library (.NET Framework)** - \\\\для линукса нужен такой же тип проекта??.
3. Укажите имя проекта. Оно должно начинаться с префикса **Primo.** Например: `Primo.My.Activity`.
4. Выберите фреймворк **.NET Framework 4.6.1**.
5. Откройте окно инструментов Solution Explorer. Добавьте в References вашего проекта следующие файлы из папки установки Primo RPA Studio (Linux):
   * LTools.Common.dll
   * LTools.Dto.dll - нужно или нет для линукс?
   * LTools.Enums.dll
   * LTools.Scripting.dll
   * LTools.SDK.dll
6. Также добавьте в ваш проект стандартные сборки: ////- их откуда брать? нужны ли они для Линукса? У Алексея в инструкции они не указаны.
   * PresentationCore
   * PresentationFramework
   * System.Xaml
   * WindowsBase


:small_blue_diamond: **Вопрос**: у Алексея в инструкции написано: "File Class1.cs needs to be deleted!".  Что это за файл, откуда берется и зачем удалять.


## Структура проекта 

Проект библиотеки (или каждого "элемента" в библиотеке?) в Visual Studio состоит из папок. Для примера создадим в проекте следующие папки:
1. Classes - классы, которые будут использоваться в элементах в целом в рамках этой библиотеки.
2. Elements - элементы, которые войдут в вашу библиотеку.
3. Images.
4. Localization - локализация.
5. Views - визуальные формы, на которые мы смотрим.

![](.gitbook/assets1/)


Вопрос: это более-менее общая структура для всех библиотек? что из этих папок обязательно, а что опционально? 


## Как что-то создать

**Как добавить в проект визуальную составляющую элемента:**

Добавьте в проект компонент типа **User Control (WPF)** (Add ➝ New Item…). Данный элемент будет являться визуальной составляющей нашего элемента Primo. Данные будущего элемента автоматически будут смаплены на DataContext данного контролла (пример будет приведен далее).

**Как создать класс элемента:**

Создайте класс (Add ➝ Class…). Данный класс будет являться code-behind нашего элемента.

Для создания элемента:
* с синхронным поведением необходимо унаследовать класс LTools.SDK.PrimoComponentSimple<UI>.
* с тайм-аутом необходим класс LTools.SDK.PrimoComponentTO<UI>.

Где UI – это имя вашего визуального компонента из шага 5.


**Как загрузить в проект изображения:**

Правой кнопкой мыши кликните по папке Images, выберите Add > Existing Item... и загрузите нужные изображения. 

Затем кликните правой кнопкой мыши каждое изображение и откройте Properties. В группе свойств Advanced выберите для Buld Action значение Resource. (зачем это делать? это всегда и для всех картинок нужно делать?)


**Как настроить название проекта (или правильнее - пакета?)**   ///и зачем это делать

В окне Solution Explorer разверните Properties проекта и дважды щелкните файл `AssemblyInfo.cs`. Затем заполните поля, как на рисунке ниже:

(Рисунок Алексея)


## Создание элемента

Правой кнопкой мыши кликните по папке Elements и выберите Add -> New Item... -> Choose C# Class. Укажите имя элемента, например, `MyFirstActivity.cs` и нажмите Add.

Далее правой кнопкой мыши кликните по папке Views и выберите Add -> New Item... -> Choose User Control (WPF) -> Name: MyFirstActivity_Form.xaml -> Add.

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

Итак, у нас определены столбцы и строки. Затем под `</Grid.RowDefinitions>` добавьте изображение: 

```
<Grid Grid.Row="0" Grid.Column="0">
  <Image HorizontalAlignment="Left" 
         Source="pack://application:,,/User.My.Activity;component/Images/eye_logo.png"
         Height="40"
         Width="40"
         Margin="5,5,5,5"
  />
</Grid>
```





## Пример кода
Сначала можно попробовать создать элемент на винде. 
Ссылка Леши: 






##










##



##
