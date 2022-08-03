# Копировать-вставить слайд

![](<../../../.gitbook/assets/image (477).png>)



Компонент, производящий копирование-вставку слайда в презентацию.

Свойства

| Свойство                 | Тип     | Описание                   |
| ------------------------ | ------- | -------------------------- |
| Индекс слайда            | Int32   | Индекс слайда              |
| Индекс слайда назначения | Int32   | Индекс слайда назначения   |
| Файл назначения          | String  | Путь к файлу назначения    |
| Перенос                  | Boolean | Осуществить перенос слайда |

{% tabs %}
{% tab title="C#" %}
```csharp
app.CopyPasteSlide(1, "C:\\file.pptx", 4, false]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.CopyPasteSlide(1, "C:\\file.pptx", 4, False)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.CopyPasteSlide(1, "C:\\file.pptx", 4, false);
```
{% endtab %}
{% endtabs %}
