# Вызов проекта

![](<../../../../.gitbook/assets/Вызов проекта.png>)

Элемент, который предназначен для вызова и локальной обработки проекта из Оркестратора. 

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство          | Тип                                                     | Описание                                    |
| ----------------- | ------------------------------------------------------- | --------------------------------------------|
| Путь к процессу\* | String                                                  | Путь к файлу процесса из нужного проекта в Оркестраторе (\file.ltw) | 
| Кешировать        | Boolean                                                 | Кэширует данные процесса для экономии памяти при вызове проекта | 
| Проект            | String                                                  | Название проекта                            | 

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





