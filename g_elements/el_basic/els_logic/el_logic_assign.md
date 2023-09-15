# Присвоение

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (11).png>)

![](<../../../.gitbook/assets/image (179).png>)

Элемент позволяет присвоить данные переменной.

При необходимости компонент можно преобразовать во [**Множественное присвоение**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/els\_logic/el\_multipleassign). Для этого вызовите контекстное меню элемента и выберите команду «Преобразовать во Множественное присвоение»:

![](<../../../.gitbook/assets/assign-context-menu.png>)

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство   | Тип | Описание                                                |
| ---------- | --- | ------------------------------------------------------- |
| Данные\*   | T   | Выражение, результат которого будет присвоен переменной |
| Переменная | T   | Переменная, которой необходимо присвоить значение       |

**Примечание**:

Тип `T` - это параметр универсального типа. О нем можно прочесть в документации Microsoft:
* [на англ. языке](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generic-type-parameters).
* [на русском](https://learn.microsoft.com/ru-ru/dotnet/csharp/fundamentals/types/generics).
