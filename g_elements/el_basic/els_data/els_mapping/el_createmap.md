# Создать маппинг

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (244).png>)

![](<../../../../.gitbook/assets/image (382).png>)

Создает маппинг переменных на аргументы вызываемой последовательности.

| Свойство     | Тип                                                                      | Описание                                           |
| ------------ | ------------------------------------------------------------------------ | -------------------------------------------------- |
| Переменная\* | [LTools.Common.Model.VariablesMapping](../datatypes/variablesmapping.md) | Переменная для хранения маппинга                   |
| Сочетания\*  | System.Collections.Generic.Dictionary                                    | Коллекция сочетаний Имя аргумента - Имя переменной |

**Дополнение:**

Также создать маппинг можно в коде, для этого можно воспользоваться, например, элементом C# Script

{% content-ref url="../../els_prog/el_prog_cs.md" %}
[el\_prog\_cs.md](../../els\_prog/el\_prog\_cs.md)
{% endcontent-ref %}

При этом сценарий может быть такой:

```
map.DeleteMapping("arg1");
map.AddMapping("arg2", new ScriptVariable() { Value = var1, Name = "var1" });
```
