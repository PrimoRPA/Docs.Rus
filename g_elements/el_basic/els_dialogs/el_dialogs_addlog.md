# Запись в журнал

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (198).png>)

![](<../../../.gitbook/assets/image (337).png>)

**«Запись в журнал» (Add to log)** - позволяет вывести сообщение в [Консоль](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#konsol) и [пользовательский журнал](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/log). RPA-разработчики и аналитики могут использовать этот элемент для отслеживания текущего состояния выполнения процесса. Просмотр пользовательских сообщений помогает удостовериться, что обработка данных в процессе происходит корректно. 

Где просмотреть записи:
1. В пользовательском журнале - текстовый файл, который хранится в папке `Log` в `AppData`. Для того, чтобы файл сохранялся, необходимо в [настройках отладчика](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#otladchik) включить параметр **Писать пользовательский журнал**. В названии журнала содержится слово **custom**, которое позволяет отличить его от журнала Студии и Робота. Пример: 2404202316_Default_Robot1_**custom**.log. 
2. В Консоли - панель в нижней части интерфейса Studio. Во время запуска/отладки процесса здесь отобразятся записи, созданные на шаге выполнения элемента **«Запись в журнал»**.

   ![](<../../../.gitbook/assets/add-to-log-console.png>)


### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство | Тип                         | Описание        |
| -------- | --------------------------- | --------------- |
| Тип\*    | LTools.Enums.LogMessageType | Тип сообщения. По умолчанию **Info** - информационное. При нажатии на выпадающий список возможно выбрать другой тип: Error, Debug, Network и т.д. |
| Текст\*  | String                      | Текст сообщения. Можно использовать переменную. Если используется переменная другого типа данных, ее нужно привести к строке |

![](<../../../.gitbook/assets/>)


### Обучающий пример

На портале Learning можно скачать процесс [Запись в журнал.ltw](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/Ru/%D0%94%D0%B8%D0%B0%D0%BB%D0%BE%D0%B3%D0%B8/%D0%97%D0%B0%D0%BF%D0%B8%D1%81%D1%8C%20%D0%B2%20%D0%B6%D1%83%D1%80%D0%BD%D0%B0%D0%BB.ltw), демонстрирующий работу элемента. Добавьте этот процесс в свой проект в Студии, чтобы просмотреть его.


### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.AddToLog(wf, "Сообщение", LTools.Enums.LogMessageType.Info);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Workflow.PrimoApp.AddToLog(wf, "Сообщение", LTools.Enums.LogMessageType.Info)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, "Сообщение", _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}
