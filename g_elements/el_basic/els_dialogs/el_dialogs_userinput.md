# Пользовательский ввод

![](<../../../.gitbook/assets/image (48).png>)

Компонент, производящий отображение пользовательского окна ввода данных.

| Свойство  | Тип    | Описание                                                                                     |
| --------- | ------ | -------------------------------------------------------------------------------------------- |
| URL\*     | String | URL отображаемого диалога (Например: http://myserver/dialog.html или file:///c:/dialog.html) |
| Ширина\*  | Int32  | Ширина отображаемого диалога                                                                 |
| Высота\*  | Int32  | Высота отображаемого диалога                                                                 |
| Результат | String | Полученные от диалога данные                                                                 |

Пример страницы диалога:

```markup
<!DOCTYPE html>
<html lang="en">
 <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <title>Primo Dialog</title>
  </head>
  <body>      
          Имя:<br>
          <input type="text" id="First_Name"><br>
          Фамилия:<br>
          <input type="text" id="Last_Name"><br>
          Возраст:<br>
          <input type="text" id="Age"><br>
          <button onclick="SubmitValues()">Отправить</button>


          <script type="text/javascript">
          function SubmitValues(){
            var First_Name = document.getElementById("First_Name").value;
            var Last_Name = document.getElementById("Last_Name").value;
            var Age = document.getElementById("Age").value;
            window.external.finished(First_Name + "," + Last_Name + "," + Age);
            return true;
          }            
          </script>
  </body>
  </html>

```

Для передачи данных роботу, необходимо вызвать функцию window.external.finished

{% tabs %}
{% tab title="C#" %}
```csharp
String res = LTools.Workflow.PrimoApp.CustomInput(wf, "url", 200, 200);
```
{% endtab %}

{% tab title="Python" %}
```python
res = LTools.Workflow.PrimoApp.CustomInput(wf, "url", 200, 200)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var res = _lib.LTools.Workflow.PrimoApp.CustomInput(wf, "url", 200, 200);
```
{% endtab %}
{% endtabs %}
