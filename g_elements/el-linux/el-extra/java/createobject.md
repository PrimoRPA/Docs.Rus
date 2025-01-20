---
Description: Create Java object
---

# Создать объект Java

![](../../../.gitbook/assets1/linux-items-extra/create-java-object-base.png)

Элемент создает объект Java с заданным типом. Для создания объекта должен использоваться класс из файла \*.jar, указанного в элементе [**Загрузить jar**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_java/el_loadjar).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

***Объект***
1. **Тип\*** *[String]* - Тип создаваемого объекта. Пример: `"package.name.ClassName"`
1. **Параметры** *[List\<object\>]* - Параметры конструктора. **Важно**: значение параметра не может быть null. 

***Вывод***
1. **Результат** *[Primo.Java.Linux.Models.JavaObject]* - Переменная вывода, которая будет хранить ссылку на созданный объект.
