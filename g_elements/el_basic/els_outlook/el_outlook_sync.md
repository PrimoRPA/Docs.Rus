# Синхронизировать папку

![](<../../../.gitbook/assets/attach_outlook.png>)

Элемент принудительно синхронизирует указанную папку Outlook. 

Компонент может пригодиться при отправке писем: сообщения в Outlook отправляются не одномоментно, а спустя какое-то время - при синхронизации папки с исходящими. Если закрыть приложение Outlook до завершения синхронизации, письмо не будет отправлено. Принудительная синхронизация позволяет избежать этого сценария.

**Общая информация**:
1. Параметры подключения к Outlook настраиваются в контейнере [Приложение Outlook](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook/el_outlook_app).
2. Элемент **Синхронизировать папку** необходимо размещать после отправки сообщения, но перед [закрытием Outlook](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook/el_outlook_close). 

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| ***Outlook:*** | |  |
| Путь к папке\*       | String                | Путь к папке Outlook. Пример: `"\\<имя_профиля>\Inbox"`. Не следует указывать только аккаунт, иначе будут синхронизироваться все папки |
| Тайм-аут             | Int32                 | Время ожидания окончания синхронизации в миллисекундах. По умолчанию 0 - робот будет столько времени, сколько потребуется для успешной синхронизации (в том числе длительно). Если указано другое значение, но синхронизация и отправка письма не завершились по истечении таймаута, в финале будет ошибка |

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
  
{% tabs %}
{% tab title="C#" %}
```csharp
//app - [LTools.Office.OutlookApp] Приложение Outlook
//folder - Путь к папке: [String] Путь к папке Outlook (\\имя_профиля\Inbox)
//to - Тайм-аут: [Int32] Тайм-аут синхронизации
//app.SyncFolder(folder, [to]);
		
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
app.SyncFolder("\\User1\Входящие", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
#app - [LTools.Office.OutlookApp] Приложение Outlook
#folder - Путь к папке: [String] Путь к папке Outlook (\\имя_профиля\Inbox)
#to - Тайм-аут: [Int32] Тайм-аут синхронизации
#app.SyncFolder(folder, [to])
		
app = LTools.Office.OutlookApp.Init(wf,  "Outlook", "password")
app.SyncFolder("\\User1\Входящие", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//app - [LTools.Office.OutlookApp] Приложение Outlook
//folder - Путь к папке: [String] Путь к папке Outlook (\\имя_профиля\Inbox)
//to - Тайм-аут: [Int32] Тайм-аут синхронизации
//app.SyncFolder(folder, [to]);
		
let app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
app.SyncFolder("\\User1\Входящие", 10000);
```
{% endtab %}
{% endtabs %}



