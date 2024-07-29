# Диалог выбора файла

*Eng: Choose file*

![](<../../../.gitbook/assets/image (469).png>)

Компонент, открывающий диалоговое окно для выбора файла. Позволяет пользователю выбрать файл на своем компьютере для загрузки или дальнейшей обработки.

### Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство    | Тип                                    | Описание                       |
| ----------- | -------------------------------------- | ------------------------------ |
| Заголовок   | String                                 | Заголовок диалогового окна           |
| Текст       | String                                 | Сопроводительный текст в диалоговом окне |
| Тип диалога | LTools.Workflow.Model. ChooseFileModes | Тип диалогового окна             |
| Ширина\*    | Int32                                  | Ширина отображаемого диалогового окна  |
| Высота\*    | Int32                                  | Высота отображаемого диалогового окна   |
| Результат   | String                                 | Полученные данные   |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)


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
