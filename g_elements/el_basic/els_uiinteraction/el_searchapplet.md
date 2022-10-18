# Поиск Java Applet

![](<../../../../.gitbook/assets/Поиск Java Applet.png>)

Элемент, производящий поиск программы Java Applet.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements).*

| Свойство             | Тип                                                               | Описание                                           |
| -------------------- | ----------------------------------------------------------------- | -------------------------------------------------- |
| ***Поиск***          |                                                                   |     |
| Таймаут\*            | Int32                                                             | Предельное время ожидания завершения процесса (мс) |
| Искомое изображение  | [System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?view=dotnet-plat-ext-6.0&viewFallbackFrom=net-5.0) | Растр искомого изображения  |
| Координаты           | [System.Drawing.Point](https://learn.microsoft.com/ru-RU/dotnet/api/system.drawing.point?view=net-6.0) | Координаты апплета                   |
| Позиция              | -                                                                 | Позиция элемента на изображении. Выберите значение из выпадающего списка  |
| Точность             | [Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?v=20.2&f=token%20edit&view=net-6.0) | Точность совпадения растра. Указывается в % от 0 до 1 |
| Область              | -                                                                 | Область поиска компонента. Нажмите на свойство, чтобы задать поиск по конкретным параметрам |
| ***Вывод***          |                                                                   |     |
| Applet               | [LTools.UIInteraction.Model.UIControl](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_uiinteraction/datatypes/uicontrol)| Переменная для сохранения найденного апплета |

  
