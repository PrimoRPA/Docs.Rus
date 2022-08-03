# Диалог выбора файла

![](<../../../.gitbook/assets/image (469).png>)



Компонент, производящий отображение окна выбора файла.

| Свойство    | Тип                                    | Описание                       |
| ----------- | -------------------------------------- | ------------------------------ |
| Заголовок   | String                                 | Заголовок диалога              |
| Текст       | String                                 | Сопроводительный текст диалога |
| Тип диалога | LTools.Workflow.Model. ChooseFileModes | Тип диалога выбора             |
| Ширина\*    | Int32                                  | Ширина отображаемого диалога   |
| Высота\*    | Int32                                  | Высота отображаемого диалога   |
| Результат   | String                                 | Полученные от диалога данные   |

{% tabs %}
{% tab title="C#" %}
```csharp
String res = LTools.Workflow.PrimoApp.ChooseFile(wf, "title", "text", LTools.Workflow.Model.ChooseFileModes.File, 100, 100);
```
{% endtab %}

{% tab title="Python" %}
```python
res = LTools.Workflow.PrimoApp.ChooseFile(wf, "title", "text", LTools.Workflow.Model.ChooseFileModes.File, 100, 100) #String
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var res = _lib.LTools.Workflow.PrimoApp.ChooseFile(wf, "title", "text", _lib.LTools.Workflow.Model.ChooseFileModes.File, 100, 100); //String
```
{% endtab %}
{% endtabs %}
