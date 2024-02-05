# Получить значение

Позволяет получить значение из строки таблицы.

![](<../../../../.gitbook/assets1/WFDataTableGetRowItem.png>)



## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Обработка**:

1. **Строка\*** *[[System.Data.DataRow](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datarow?view=net-8.0&viewFallbackFrom=net-4.6.1)]* - строка таблицы.
1. **Столбец** *[[System.Data.DataColumn](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datacolumn?view=net-8.0&viewFallbackFrom=net-4.6.1)]* - столбец таблицы.
1. **Имя** *[String]* - название столбца.
1. **Индекс** *[Int32]* - номер столбца.

**Вывод**:

1. **Значение\*** *[T]* - значение из таблицы.

