---
description: Get asset
---

# Получить ресурс

![Внешний вид элемента](<../../../../.gitbook/assets1/windows_items/WFGetAsset.png>)

Элемент позволяет получить [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-user/robots/assets) из Оркестратора. Поиск ресурса осуществляется по его названию. Поддерживается работа с ресурсами следующих типов данных:
* String
* Integer
* Floating
* Boolean
* DateTime
* JObject (для JSON)

Полученный ресурс робот сохранит в переменную с типом данных `System.Object`, название которой указывается в свойстве **Результат**.

> **Примечание**.
> 1. До версии 1.24.6 элемент **Получить ресурс** назывался **Получить значение**.
> 2. Чтобы получить ресурс с типом Credentials, используйте элемент [Получить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_getcredentials).


## Начальные условия

* Установлено [подключение](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator) Студии к Оркестратору.
* В Оркестраторе создан ресурс поддерживаемого типа данных.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                                                             |
| -------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Наименование\* | String | Название ресурса в Оркестраторе, значение которого вы хотите получить. Учитывается регистр. Пример: `"MyAsset"` |
| Таймаут        | Int32  | Лимит времени выполнения операции в миллисекундах. По умолчанию `5000`. Если по истечении таймаута операция не выполнена, робот закончит работу с ошибкой |
| Результат      | Object | Название переменной для хранения значения ресурса             |


## Решение проблем

При выполнении элемента может возникнуть «Ошибка получения значения». Она возникает, если ресурса с указанным названием нет в Оркестраторе.


## Пример использования



Пример использования элемента **Получить ресурс** доступен в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

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
