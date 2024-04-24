---
description: Invoke project
---


# Вызов проекта

Элемент вызывает проект из Оркестратора, чтобы обработать его локально. В свойствах элемента необходимо указать название проекта, загруженного в Оркестратор, и стартовый процесс для запуска. 

Предварительные условия:
* Вызываемый проект должен быть добавлен в Оркестратор. Если проект имеет несколько версий в Оркестраторе, то будет использоваться активная версия.
* Студия должна быть подключена к Оркестратору.

![Элемент «Вызов проекта»](<../../../../.gitbook/assets/Вызов проекта.png>)

Если в вызываемом процессе есть аргументы, воспользуйтесь кнопкой ![](<../../../../.gitbook/assets/args-link-process2.png>) на панели элемента, чтобы настроить их. При нажатии кнопки откроется окно вида:

![Диалог с аргументами](<../../../../.gitbook/assets/args-window.png>)

В данном окне отобразятся все аргументы, которые есть в вызываемом процессе. Изменить название аргумента или его направление в этом окне нельзя.



   
## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство          | Тип                                                     | Описание                                     |  Пример        |  
| ----------------- | ------------------------------------------------------- | -------------------------------------------- | -------------- |
| Проект            | String                                                  | Название проекта в Оркестраторе, который вы хотите вызвать. Соблюдайте регистр | `"TotalSalary"`  |
| Путь к процессу\* | String                                                  | Путь к файлу стартового процесса из проекта Оркестратора | `@"\file.ltw"` <p></p>  <p>Символ `@` позволяет не экранировать обратную косую черту в строке </p> |
| Кешировать        | Boolean                                                 | Определяет, нужно ли кешировать данные процесса. Кеширование сэкономит память при вызове проекта. По умолчанию данные не кешируются |  |



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





