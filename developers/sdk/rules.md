# Создание правила анализа кода


## Начало работы

1.	Запустить Visual Studio.
2.	Выбрать **Create a new project** с типом Class Library (.NET Framework) либо Class Library (поддерживаются .NET Framework 4.6.1 и .NET Standard 2.0).
3.	Ввести имя проекта. ***Важно! Имя проекта и библиотеки dll должны начинаться с “Primo.”***
4.	Добавить в References проекта сборку Primo.ProjectAnalyzer.Dto.dll:

   ![](<../../.gitbook/assets/1.sdk.rules.png>) 

5\.	Создайте класс (Add -> Class…), который будет содержать правило. Для этого надо унаследовать интерфейс Primo.ProjectAnalyzer.IAnalysisRule.

## Создание правила


![](<../../.gitbook/assets/2.sdk.rules.png>) 

![](<../../.gitbook/assets/3.sdk.rules.png>) 
 
