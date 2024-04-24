---
description: Get asset
---


# Получить значение

Элемент позволяет получить [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) из Оркестратора. Поиск ресурса осуществляется по его названию. Полученный ресурс необходимо сохранить в свойстве **Результат** в виде переменной. Она должна иметь тип данных System.Object.

![Элемент «Получить значение»](<../../../../.gitbook/assets/image (269).png>)

Робот может запросить ресурс следующих типов данных:
* String;
* Integer;
* Floating;
* Boolean;
* DateTime;
* JObject (для JSON).

:small_orange_diamond: ***Чтобы получить ресурс с типом Credentials, используйте элемент [Получить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_getcredentials).***


## Начальные условия

:small_blue_diamond: Установлено [подключение](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator) Студии к Оркестратору.\
:small_blue_diamond: В Оркестраторе добавлены ресурсы указанных типов.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                                                             |
| -------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Наименование\* | String | Название ресурса в Оркестраторе, значение которого хотите получить. Соблюдайте регистр. Пример: `"MyAsset"` |
| Таймаут        | Int32  | Лимит времени выполнения операции в миллисекундах. По умолчанию `5000`. Если по истечении таймаута операция не выполнена, робот закончит работу с ошибкой |
| Результат      | Object | Название переменной для хранения значения ресурса             |


### Решение проблем

![](<../../../../.gitbook/assets1/set-asset-error-in-studio.png>)

При выполнении элемента может возникнуть «Ошибка получения значения». Она возникает, если ресурса с указанным названием нет в Оркестраторе.



## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Выберите процесс `StudioActivities/Ru/Оркестратор/Значения/Значения.ltw` для просмотра.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
object ret = LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key");
```
{% endtab %}
{% endtabs %}
