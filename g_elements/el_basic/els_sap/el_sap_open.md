# Открыть SAP

![](<../../../.gitbook/assets/image (361).png>)

Элемент осуществляет подключение к SAP Front End.

## Свойства
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` указывает на обязательность заполнения свойства.

| Свойство           | Тип                | Описание                                                 |
| ------------------ | ------------------ | -------------------------------------------------------- |
| ***SAP Front End:*** | | | 
| Соединение\*       | String             | Наименование соединения в SAP Logon                      |
| Клиент\*           | String             | Номер клиента (000-999)                                  |
| Логин\*            | String             | Логин пользователя                                       |
| Пароль             | String             | Пароль пользователя                                      |
| Защищенный пароль |[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=netcore-2.0) | Если пароль используется в зашифрованном виде, укажите его в этом поле. В целях безопасности пароль в формате SecureString не хранится в открытом виде даже в памяти компьютера. Получить его можно, например, из **Диспетчера учетных данных** (Credential Manager) |
| Язык подключения\* | String             | Язык подключения. По умолчанию установлен "en" - английский |
| Переменная         | [LTools.SAP.SAPInst](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_sap/datatypes/sapinst) | Переменная, содержащая ссылку на подключенный процесс. Полезно, если в одном процессе Вы используете несколько элементов **Открыть SAP**. Например, в первом элементе Вы сохранили ссылку на подключенный процесс в переменной вывода, а во втором указали ее в этом поле для более быстрого подключения |
| ***Запуск:*** |  |  |
| Запускать          | Boolean            | Определите, нужно ли запускать SAP средствами Explorer. Если да, установите отметку |
| Путь               | String             | Путь к saplogon.exe. По умолчанию установлено значение `"C:\\Program Files (x86)\\SAP\\FrontEnd\\SapGui\\saplogon.exe"` |
| Тайм-аут           | Int32              | Время ожидания старта (мс). По умолчанию **10000**       |
| ***Вывод:***  |  |  |
| Переменная         | [LTools.SAP.SAPInst](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_sap/datatypes/sapinst) | Укажите переменную, в которой будет храниться ссылка на подключенный процесс |

## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf, "test2", "001", "DEVELOPER", "Appl1ance", "en");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf, "test2", "001", "DEVELOPER", "Appl1ance", "en")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf, "test2", "001", "DEVELOPER", "Appl1ance", "en");
```
{% endtab %}
{% endtabs %}
