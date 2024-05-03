# Начало работы

1. Запустить Visual Studio.
2. Выбрать **Create a new project** с типом проекта Class Library (.NET Framework).
3. Ввести имя проекта. **ВНИМАНИЕ!** **Имя проекта и библиотеки dll должны начинаться с префикса "Primo.".** 
4. Выбрать фреймворк .NET Framework 4.6.1.
5. Добавить в References проекта сборки:
   * _LTools.Common.dll_
   * _LTools.Dto.dll_
   * _LTools.Enums.dll_
   * _LTools.Scripting.dll_
   * _LTools.SDK.dll_

   Найти эти сборки можно в папке Primo Studio.

   Также добавьте стандартные сборки:

   * _PresentationCore_
   * _PresentationFramework_
   * _System.Xaml_
   * _WindowsBase_

   ![](<../../../.gitbook/assets/0 (133).png>)

6\. Добавьте в проект компонент типа **User Control (WPF)** (Add ➝ New Item…)

![](<../../../.gitbook/assets/1 (118).png>)

   Данный элемент будет являться визуальной составляющей нашего элемента Primo. Данные будущего элемента автоматически будут смаплены на DataContext данного контролла (пример будет приведен далее).

7\. Создайте класс (Add ➝ Class…). Данный класс будет являться code-behind нашего элемента.

8\. Для создания элемента с синхронным поведением необходимо унаследовать класс **LTools.SDK.PrimoComponentSimple\<UI>**. 

Для создания элемента с тайм-аутом необходим класс **LTools.SDK.PrimoComponentTO\<UI>**.

Где **UI – это имя вашего визуального компонента из шага 6**.
