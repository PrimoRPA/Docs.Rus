# Ссылка на процесс

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (54).png>)

![](<../../../.gitbook/assets/image (211).png>)

Элемент выполняет процесс, указанный в ссылке (или, иначе, подпроцесс).

На панели элемента находятся кнопки:

1. **Открыть** ![](<../../../.gitbook/assets/open-link-process2.png>) - нажатие на кнопку автоматически открывает вкладку с указанным подпроцессом.
2. **Аргументы** ![](<../../../.gitbook/assets/args-link-process2.png>) - вызывает окно с аргументами подпроцесса. Пример:

   ![](<../../../.gitbook/assets/args-window.png>)

   Для каждого из аргументов возможно создать свою переменную/аргумент для указания в столбце **Назначение**. В окне поддерживается сочетание клавиш:
   * `Ctrl` + `K` - для создания переменной. Переменная создается для выбранного аргумента в соответствии с его типом данных. Добавленная переменная отобразится в столбце **Назначение**, а также на панели переменных активного процесса.
   * `Ctrl` + `Alt` + `K` - для создания аргумента. Тип данных назначается в соответствии с выбранным аргументом подпроцесса. 

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                                                                 | Описание                                             |
| -------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------- |
| ***Процесс:***       |                                                                                     |                                                      |
| Путь к процессу\*    | String                                                                              | Путь к файлу подпроцесса. Пример: `"C:\\Users\\Username\\Folder\\Primo\\Project\\file.ltw"` |
| Маппинг\*            | [LTools.Common.Model. VariablesMapping](../els\_data/datatypes/variablesmapping.md) | Маппинг аргументов подпроцесса                       |
| Кешировать           | Boolean                                                                             | Определите, нужно ли кешировать подпроцесс           |
| ***Песочница:***     |                                                                                     |                                                      |
| Запуск в песочнице   | Boolean                                                                             | Нужно ли запускать процесс в песочнице Windows |
| Закрывать            | Boolean                                                                             | Нужно ли закрывать песочницу по завершении. По умолчанию закрывается |
| Таймаут старта\*     | Int32                                                                               | Таймаут запуска песочницы в миллисекундах. По умолчанию `60000` |
| Таймаут завершения\* | Int32                                                                               | Таймаут завершения работы робота в миллисекундах (0 - бесконечно). По умолчанию `0` |
| Параллельно          | Boolean                                                                             | Нужно ли запускать песочницу параллельно с основным процессом |


## Пример использования

Перейдите по [ссылке](https://github.com/PrimoRPA/Learning/tree/master/StudioActivities/Ru/%D0%A3%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5), чтобы скачать процессы, демонстрирующие работу элемента. Они имеют названия `Ссылка на процесс.ltw` и `Ссылка на процесс 1.ltw` (подпроцесс). Чтобы ознакомиться с работой процессов, загрузите их в нужный проект и откройте в Студии.
 
## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
