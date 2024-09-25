---
description: Type simulate
---

# Эмуляция ввода текста

![Внешний вид элемента](<../../../.gitbook/assets/image (243).png>)

Элемент имитирует пользовательский ввод текста с клавиатуры. Для корректной работы поместите элемент в контейнер [Присоединиться к приложению](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_attach).


## Свойства

Обязательные для заполнения свойства отмечены символом `*`. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Текст** *[String]* — строка для ввода. Пример: `"test text"`.
1. **Пауза\*** *[Int32]* — пауза между нажатиями клавиш, указывается в миллисекундах. По умолчанию `500`. Пауза игнорируется, если установлена галочка в свойстве **Новое ядро** — в этом случае задержки при вводе не будет.
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса, указывается в миллисекундах. По умолчанию `10000`. Если процесс не завершился в установленное время, возникнет ошибка.
1. **Асинхронный** *[Boolean]* — определяет, следует ли использовать асинхронный ввод.
1. **Новое ядро** *[Boolean]* — определяет, следует ли использовать новое ядро для взаимодействия с операционной системой. По умолчанию новое ядро не используется. Данное свойство рекомендуется включать, если вы столкнулись с какой-либо проблемой при имитации ввода — например, если не эмулируется подчеркивание. 
1. **Защищенный текст** *[[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=net-5.0)]* — защищенная строка. Данное свойство предназначено, если вы хотите имитировать ввод конфиденциальных данных, и вам не подходит свойство **Текст**. 


## Пример использования

Пример процесса, который демонстрирует использование элемента, доступен в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект из папки **StudioActivities**.
3. Откройте процесс `Эмуляция ввода текста.ltw`.




## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
LTools.Desktop.DesktopApp.TypeSimulate(wf, "Text", 100, 20000);	
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
LTools.Desktop.DesktopApp.TypeSimulate(wf, "Text", 100, 20000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
_lib.LTools.Desktop.DesktopApp.TypeSimulate(wf, "Text", 100, 20000);	
```
{% endtab %}
{% endtabs %}
