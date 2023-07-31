# Пользовательский ввод

![](<../../../.gitbook/assets/image (321).png>)

Элемент отображает пользовательское окно ввода данных.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство  | Тип    | Описание                                                                                     |
| --------- | ------ | -------------------------------------------------------------------------------------------- |
| URL\*     | String | URL отображаемого диалога. Пример: `"http://myserver/dialog.html"` или `@"C:\Users\Username\Desktop\dialog.html"`. Значок @ используется для экранирования символа `\` |
| Ширина\*  | Int32  | Ширина отображаемого диалога                                                                 |
| Высота\*  | Int32  | Высота отображаемого диалога                                                                 |
| Результат | String | Переменная с полученными от диалога данными                                                  |

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

Для передачи данных роботу необходимо вызвать функцию window.external.finished

## Обучающий пример

Пример последовательности, в котором демонстрируется использование элемента **Пользовательский ввод**, можно скачать [ссылке](https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/Ru/%D0%94%D0%B8%D0%B0%D0%BB%D0%BE%D0%B3%D0%B8/%D0%9F%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D1%81%D0%BA%D0%B8%D0%B9%20%D0%B2%D0%B2%D0%BE%D0%B4.ltw). Загрузите скачанный процесс в студийный проект, чтобы просмотреть его.

## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

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
