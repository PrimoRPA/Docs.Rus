# ExecutionExceptionInfo

LTools.Common.Model.ExecutionExceptionInfo - информация об исключении.

:small_blue_diamond: **Примечание**. Знак «?» в типе данных указывает на то, что значение может быть null.

| Свойство     | Тип      | Описание            |
| ------------ | -------- | ------------------- |
| Timestamp    | DateTime | Время исключения    |
| Message      | String   | Сообщение           |
| ComponentID  | Guid?    | ID элемента         |
| WorkflowPath | String   | Выполняемый процесс |
| ExceptionType | LTools.Common.Model.ExceptionTypes | Тип исключения |
| ExceptionClass | String | Имя класса исключения |
| Code         | Int      | Код исключения      |
