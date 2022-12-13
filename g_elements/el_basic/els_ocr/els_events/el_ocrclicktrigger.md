# Событие клика изображения

![](<../../../../.gitbook/assets/image (134).png>)



Компонент, ожидающий событие клика на изображении.

| Свойство              | Тип                                | Описание                                 |
| --------------------- | ---------------------------------- | ---------------------------------------- |
| Искомое изображение   | [System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?redirectedfrom=MSDN&view=netframework-4.8)              | Растр искомого изображения               |
| Точность              | [Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)                             | Точность совпадения растра (% от 0 до 1) |
| Основная кнопка       | LTools.Common.Model. MouseButtons  | Основная кнопка                          |
| Модификатор           | System.Windows.Input. ModifierKeys | Кнопка-модификатор (Ctrl, Shift...)      |
| Дополнительная кнопка | System.Windows.Input. ModifierKeys | Дополнительная кнопка                    |
| Блокировать           | Boolean                            | Блокировать действие                     |
