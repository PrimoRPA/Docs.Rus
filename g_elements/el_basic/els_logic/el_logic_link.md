# Ссылка на процесс

![](<../../../.gitbook/assets/image (100) (1) (7).png>)

![](<../../../.gitbook/assets/image (211).png>)

Компонент, производящий выполнение процесса, указанного в ссылке.

При нажатии на кнопку Открыть, автоматически открывается закладка с указанным в свойствах процессом.

| Свойство             | Тип                                                                                 | Описание                                             |
| -------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------- |
| Путь к процессу\*    | String                                                                              | Путь к файлу процесса (c:\folder\file.ltw)           |
| Маппинг\*            | [LTools.Common.Model. VariablesMapping](../els\_data/datatypes/variablesmapping.md) | Маппинг аргументов                                   |
| Запуск в песочнице   | bool                                                                                | Запускать процесс в песочнице Windows                |
| Закрывать            | bool                                                                                | Закрывать песочницу по завершении                    |
| Таймаут старта\*     | Int32                                                                               | Таймаут запуска песочницы                            |
| Таймаут завершения\* | Int32                                                                               | Таймаут завершения работы робота (0 - бесконечно)    |
| Параллельно          | bool                                                                                | Запускать песочницу параллельно с основным процессом |

{% tabs %}
{% tab title="C#" %}
```csharp
//Создаем аргументы
List<LTools.Workflow.Model.SequenceLinkArg> args = new List<LTools.Workflow.Model.SequenceLinkArg>();
args.Add(new LTools.Workflow.Model.SequenceLinkArg() { Name = "arg1", Value = "val1" });
//Вызываем процесс
args = LTools.Workflow.Elements.WFSequenceLink.CallWorkflow(wf, @"C:\Project\Process.ltw", args);
//Получаем аргументы
string ret = args.Where(it => it.Name == "arg1").FirstOrDefault().Value as string;
```
{% endtab %}

{% tab title="Python" %}
```python
#Создаем аргументы
args = List[LTools.Workflow.Model.SequenceLinkArg]()
args.Add(LTools.Workflow.Model.SequenceLinkArg("arg1", "val1"))
#Вызываем процесс
args = LTools.Workflow.Elements.WFSequenceLink.CallWorkflow(wf, "C:\\Project\\Process.ltw", args)
#Получаем аргументы
ret = ret[0].Value
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let host = new _lib.Microsoft.ClearScript.HostFunctions();
//Создаем аргументы
let args = host.newObj(_lib.System.Collections.Generic.List(_lib.LTools.Workflow.Model.SequenceLinkArg));
args.Add(new _lib.LTools.Workflow.Model.SequenceLinkArg("arg1", "val1"));
//Вызываем процесс
args = _lib.LTools.Workflow.Elements.WFSequenceLink.CallWorkflow(wf, "C:\\Project\\Process.ltw", args, false);
//Получаем аргументы
let ret = args[0];
```
{% endtab %}
{% endtabs %}
