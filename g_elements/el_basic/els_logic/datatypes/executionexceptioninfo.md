# ExecutionExceptionInfo

LTools.Common.Model.ExecutionExceptionInfo

| Свойство     | Тип      | Описание            |
| ------------ | -------- | ------------------- |
| Timestamp    | DateTime | Время исключения    |
| Message      | String   | Сообщение           |
| ComponentID  | Guid?    | ID элемента         |
| WorkflowPath | String   | Выполняемый процесс |
| StackTrace   | String   | Cтек вызова исключения. Позволяет увидеть всю историю вызовов исключений и благодаря этому определить источник ошибки |
