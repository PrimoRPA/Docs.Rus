# Приложение Outlook

![](<../../../.gitbook/assets/image (190).png>)

Компонент осуществляет подключение к приложению Outlook. Является контейнером для других элементов группы Outlook.

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство    | Тип    | Описание                      |
| ----------- | ------ | ----------------------------- |
| ***Outlook:*** |  |  |
| Имя профиля | String | Имя почтового [профиля](https://support.microsoft.com/ru-ru/office/%D0%BE%D0%B1%D0%B7%D0%BE%D1%80-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B0%D1%86%D0%B8%D0%B9-%D1%8D%D0%BB%D0%B5%D0%BA%D1%82%D1%80%D0%BE%D0%BD%D0%BD%D0%BE%D0%B9-%D0%BF%D0%BE%D1%87%D1%82%D1%8B-microsoft-outlook-9073a8ac-c3d6-421d-b5b9-fcedff7642fc). По умолчанию: `"Outlook"` - стандартное название профиля, если он один |
| Пароль      | String | Пароль профиля при его наличии. Чаще всего отсутствует       |
| Защищенный пароль |[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=netcore-2.0) | Если у профиля есть пароль, и он зашифрован, вставьте его в это поле. В целях безопасности пароль в формате SecureString не хранится в открытом виде даже в памяти компьютера. Получить его можно, например, из программы **Диспетчер учетных данных** (Credential Manager) |
| ***Вывод:*** |  |  |
| Переменная  | LTools.Office.OutlookInst | Переменная, которая будет хранить ссылку на установленное подключение  |

### Обучающий пример
Пример использования основных элементов Outlook можно найти [здесь](https://github.com/PrimoRPA/Learning/tree/master/StudioActivities/Ru/%D0%9F%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5%20Outlook). Файл процесса **Основное.ltw** требуется скачать и добавить в проект Студии, чтобы он стал доступен для просмотра. 

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}
{% endtabs %}
