# Документ Word

![](<../../../.gitbook/assets/image (169).png>)

Компонент производит подключение к приложению Word. В случае отсутствия указанного файла будет создан новый.

В режиме Interop не поддерживается работа с Microsoft Office 2010. Необходима более новая версия Microsoft Office.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.


| Свойство      | Тип                               | Описание                                          |
| ------------- | --------------------------------- | ------------------------------------------------- |
| Путь к файлу  | String                            | Путь к файлу документа Word (c:\folder\file.docx) |
| Пароль        | String                            | Пароль для открытия защищенного документа         |
| Пароль (зашифрованный) | SecureString             | Зашифрованный пароль от документа. В целях безопасности пароль в формате SecureString не хранится в открытом виде. Получить его можно, например, из программы «Диспетчер учетных данных» (Credential Manager), после чего вставить в это поле |
| Драйвер       | LTools.Office.Model.InteropTypes  | Тип драйвера подключения: DX или Interop          |
| Массив байтов | byte\[]                           | Массив байтов документа                           |


## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, System.IO.File.ReadAllBytes("file"), LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app = LTools.Office.WordApp.Init(wf, System.IO.File.ReadAllBytes("file"), LTools.Office.Model.InteropTypes.DX)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
var app = _lib.LTools.Office.WordApp.Init(wf, _lib.System.IO.File.ReadAllBytes("file"), _lib.LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}
{% endtabs %}
