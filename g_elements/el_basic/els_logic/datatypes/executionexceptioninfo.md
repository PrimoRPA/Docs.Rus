# ExecutionExceptionInfo

LTools.Common.Model.ExecutionExceptionInfo - информация об исключении.

:small_blue_diamond: **Примечание**. Знак «?» в типе данных указывает на то, что значение может быть null.

| Свойство     | Тип      | Описание            |
| ------------ | -------- | ------------------- |
| Timestamp    | DateTime | Время исключения    |
| Message      | String   | Сообщение           |
| ComponentID  | Guid?    | ID элемента         |
| WorkflowPath | String   | Выполняемый процесс |
| StackTrace   | String   | Cтек вызова исключения. Позволяет увидеть всю историю вызовов исключений и благодаря этому определить источник ошибки |
| Data         | [Dictionary](https://learn.microsoft.com/ru-ru/dotnet/api/system.collections.generic.dictionary-2?view=netframework-4.0) | Произвольные данные об исключении |
