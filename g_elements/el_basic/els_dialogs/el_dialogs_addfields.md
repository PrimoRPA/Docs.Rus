# Добавить поля журнала

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (2) (220).png>)

![](<../../../.gitbook/assets/Добавить поля журнала.png>)

Позволяет добавить дополнительные поля в журнал Робота Оркестратора.

> _Описание общих свойств элемента см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство | Тип                         | Описание        |
| -------- | --------------------------- | --------------- |
| Поля\*   | [Dictionary<string, string>](https://learn.microsoft.com/ru-ru/dotnet/api/system.collections.generic.dictionary-2?view=net-5.0) | Массив полей, которые нужно добавить в журнал. Пример: new Dictionary<string, string>() { { "key", "\\"value\\"" } } |

Впоследствии можно удалить ненужные поля при помощи компонента [**Удалить поля журнала**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_dialogs/el_dialogs_removefields).
