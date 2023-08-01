# Ссылка на процесс

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (54).png>)

![](<../../../.gitbook/assets/image (211).png>)

Компонент выполняет процесс, указанный в ссылке (или, иначе, подпроцесс).

На панели элемента находятся кнопки:

1. **Открыть** ![](<../../../.gitbook/assets/open-link-process.png>) - нажатие на кнопку автоматически открывает закладку с процессом, указанным в свойствах.
2. **Аргументы** ![](<../../../.gitbook/assets/args-link-process.png>) - нажатие вызывает окно с аргументами подпроцесса. С версии 23.7 допустимо использовать горячие клавиши:
   * для создания переменной - `Ctrl` + `K`. Тип данных переменной будет соответствовать выбранному аргументу. Созданная переменная отобразится на панели переменных.
   * для создания аргумента - `Ctrl` + `Alt` + `K`.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                                                                 | Описание                                             |
| -------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------- |
| ***Процесс:***       |                                                                                     |                                                      |
| Путь к процессу\*    | String                                                                              | Путь к файлу процесса (c:\folder\file.ltw)           |
| Маппинг\*            | [LTools.Common.Model. VariablesMapping](../els\_data/datatypes/variablesmapping.md) | Маппинг аргументов                                   |
| Кешировать           | Boolean                                                                             | Определите, нужно ли кешировать процесс              |
| ***Песочница:***     |                                                                                     |                                                      |
| Запуск в песочнице   | Boolean                                                                             | Запускать процесс в песочнице Windows                |
| Закрывать            | Boolean                                                                             | Закрывать песочницу по завершении                    |
| Таймаут старта\*     | Int32                                                                               | Таймаут запуска песочницы                            |
| Таймаут завершения\* | Int32                                                                               | Таймаут завершения работы робота (0 - бесконечно)    |
| Параллельно          | Boolean                                                                             | Запускать песочницу параллельно с основным процессом |


## Пример использования

Перейдите по [ссылке](https://github.com/PrimoRPA/Learning/tree/master/StudioActivities/Ru/%D0%A3%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5), чтобы скачать процессы, демонстрирующие работу элемента. Они имеют названия `Ссылка на процесс 1.ltw` и `Ссылка на процесс.ltw`. Чтобы просмотреть процессы, загрузите их в нужный проект и откройте в Студии.
 
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
