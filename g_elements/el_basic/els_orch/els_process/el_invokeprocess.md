---
description: Invoke project
---


# Вызов проекта

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (126).png>)

![](<../../../../.gitbook/assets/Вызов проекта.png>)

Элемент предназначен для вызова и локальной обработки проекта из Оркестратора. 

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство          | Тип                                                     | Описание                                     |  Пример        |  
| ----------------- | ------------------------------------------------------- | -------------------------------------------- | -------------- |
| Путь к процессу\* | String                                                  | Путь к файлу процесса из проекта в Оркестраторе      | `@"\Main.ltw"` |
| Проект            | String                                                  | Название проекта, который был загружен в Оркестратор | `"My_project"`  |
| Кешировать        | Boolean                                                 | Определяет, нужно ли кэшировать данные процесса для экономии памяти при вызове проекта. По умолчанию данные не кэшируются |  |


## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
List<LTools.Workflow.Model.SequenceLinkArg> args = new List<LTools.Workflow.Model.SequenceLinkArg>();
args.Add(new LTools.Workflow.Model.SequenceLinkArg("arg1", "value"));
List<LTools.Workflow.Model.SequenceLinkArg> ret = LTools.Workflow.Elements.WFInvokeProcess.CallWorkflow(wf, @"\Main.ltw", "Project Name", args);
```
{% endtab %}

{% tab title="Python" %}
```python
args = List[LTools.Workflow.Model.SequenceLinkArg]()
		args.Add(LTools.Workflow.Model.SequenceLinkArg("arg1", "value"))
		args = LTools.Workflow.Elements.WFInvokeProcess.CallWorkflow(wf, "\Main.ltw", "Project Name", args)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let host = new _lib.Microsoft.ClearScript.HostFunctions();
		let args = host.newObj(_lib.System.Collections.Generic.List(_lib.LTools.Workflow.Model.SequenceLinkArg));
		args.Add(new _lib.LTools.Workflow.Model.SequenceLinkArg("arg1", "value"));
		args = _lib.LTools.Workflow.Elements.WFInvokeProcess.CallWorkflow(wf, "\\Main.ltw", "Project Name", args, false);
```
{% endtab %}
{% endtabs %}





