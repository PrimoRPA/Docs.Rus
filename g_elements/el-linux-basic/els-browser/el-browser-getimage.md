---
description: Browser - Get image
---

# Скачать изображение

![Превью активности](../../resources/basic/browser/browser-getimage-preview.png)

Компонент, производящий получение изображения. Компонент может работать как внутри контейнеров "Открыть браузер" и "Присоединиться к браузеру", так и как отдельная активность.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Шаблон поиска** *[String]* - Шаблон поиска элемента управления.  
1. **Элемент** *[LTools.WebBrowser.Model.IElementInfo]* - Ссылка на элемент управления.  
1. **Атрибут** *[String]* - Название атрибута элемента управления, содержащего URL изображения.  
1. **Изображение\*** *[byte\[]]* - Переменная для сохранения данных полученного изображения.  
1. **URL** *[String]* - URL изображения.  
1. **Игнорировать сертификат** *[Boolean]* - Признак отсутствия проверки сертификата сервера.  
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс).  

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):  

{% tabs %}  
{% tab title="C#" %} 
```csharp  
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);  
//По атрибуту  
byte[] img = app.GetImage("{\"Tag\":\"IMG\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"lazyImg\"}]}", "src");  
//По URL  
img = LTools.WebBrowser.BrowserApp.GetImage(wf, "https://i0.mail.com/mcom/574/10358574%2Cpd=2%2Cf=teaser-card-s/.jpg");  
System.IO.File.WriteAllBytes(@"C:\image.png", img);  
```
{% endtab %}  

{% tab title="Python" %}  
```python  
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)  
#По атрибуту  
img = app.GetImage("{\"Tag\":\"IMG\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"lazyImg\"}]}", "src")  
#По URL  
img = LTools.WebBrowser.BrowserApp.GetImage(wf, "https://i0.mail.com/mcom/574/10358574%2Cpd=2%2Cf=teaser-card-s/.jpg")  
System.IO.File.WriteAllBytes("C:\\image.png", img)  
```
{% endtab %}  

{% tab title="JavaScript" %}  
```javascript  
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);  
//По атрибуту  
var img = app.GetImage("{\"Tag\":\"IMG\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"lazyImg\"}]}", "src");  
//По URL  
img = _lib.LTools.WebBrowser.BrowserApp.GetImage(wf, "https://i0.mail.com/mcom/574/10358574%2Cpd=2%2Cf=teaser-card-s/.jpg");  
_lib.System.IO.File.WriteAllBytes("C:\\image.png", img);  
```
{% endtab %}  
{% endtabs %}  
