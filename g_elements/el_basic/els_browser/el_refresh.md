# Обновить браузер
# **Refresh** 

Элемент представляет собой действие, которое позволяет обновить страницу в веб-браузере.



![](<../../../.gitbook/assets/image (414).png>)

В процессе роботизации использование данного элемента может понадобиться, если необходимо регулярно мониторить изменения на каком-либо веб-ресурсе.

Основные свойства элемента:

 **Продолжить при исключении (Continue on Exception)**: Данный параметр определяет, следует ли продолжить выполнение процесса в случае возникновения исключения во время обновления браузера.

 **Отключить журналирование (Disable Logging)**: Если этот параметр включен, то действие не будет записано в лог робота. 

 **Ожидание после (Wait After)**: Этот параметр позволяет установить задержку (в миллисекундах) после выполнения активности "Обновить браузер". 

 **Ожидание перед (Wait Before)**: Этот параметр определяет задержку (в миллисекундах) перед выполнением активности "Обновить браузер". Необходимо, чтобы убедиться, что все предыдущие действия завершены перед обновлением страницы.


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE);
app.Refresh();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE)
app.Refresh()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Open(wf, _lib.LTools.WebBrowser.Model.BrowserTypes.IE);
app.Refresh();
```
{% endtab %}
{% endtabs %}
