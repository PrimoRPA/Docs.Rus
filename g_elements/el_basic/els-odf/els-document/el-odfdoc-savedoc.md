# Сохранить документ

![](<../../../../.gitbook/assets1/Cropped-SaveDocument.png>)

Компонент сохраняет файл Word. Если путь к файлу не указан, сохранение будет произведено в файл текущего контейнера Word.

## Формат записи файла

Формат сохранения определяется следующим образом:
1. Если файл существует, делается попытка определить его формат, и, если формат успешно определен и поддерживается, в этом формате документ и будет сохранен. Иначе выполняется п.2
2. Формат определяется по расширению файла. В случае успеха документ сохраняется, иначе выполняется п. 3
3. Документ сохраняется в формате ".odt"

## Свойства

1. **Путь к файлу** *[String]*: Путь к файлу Word (c:\folder\files.docx).

## Только код

Пример использованиѝ элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.Save();
app.SaveAs("fileName");
```
{% endtab %}

{% tab title="Python" %}
```python
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName")
app.Save()
app.SaveAs("fileName")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.Save();
app.SaveAs("fileName");
```
{% endtab %}
{% endtabs %}

