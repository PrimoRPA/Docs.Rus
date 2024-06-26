# Заменить текст

Элемент заменяет все вхождения исходного текста на новый. Путь до файла указывается в контейнере «Документ ODF».

![](<../../../../.gitbook/assets1/windows_items/odf-text-replace.png>)


## Свойства
Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Исходный текст** *[String]* — текст, подлежащий замене.
2. **Новый текст\*** *[String]* — новый текст.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");  
app.ReplaceText(oldText, newText);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
