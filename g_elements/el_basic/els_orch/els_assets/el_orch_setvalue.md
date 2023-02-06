# Установить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (149).png>)

![](<../../../../.gitbook/assets/image (305).png>)

Компонент, производящий установку значения в Оркестратор.\
Описание общих свойств см. в разделе [Работа с элементами](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements). Утилитарные свойства приведены в таблице ниже.

| Свойство       | Тип    | Описание                 |
| -------------- | ------ | ------------------------ |
| Наименование\* | String | Наименование значения    |
| Значение\*     | Object | Устанавливаемое значение |
| Таймаут        | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.OrchestratorApp.AssetSet(wf, "Key", "data");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Enterprise.OrchestratorApp.AssetSet(wf, "Key", "data")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Enterprise.OrchestratorApp.AssetSet(wf, "Key", "data");
```
{% endtab %}
{% endtabs %}
