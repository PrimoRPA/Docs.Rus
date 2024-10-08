---
description: Read console
---

# Прочитать консоль

![Внешний вид элемента Прочитать консоль](<../../../.gitbook/assets/Прочитать консоль.png>)

Элемент извлекает информацию из консольных приложений. Может быть полезен для автоматизации задач, связанных с обработкой текстового вывода в консоли.


## Свойства
Обязательные для заполнения свойства отмечены символом `*`. Описание группы общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Диапазон**

1. **Консоль\*** *[LTools.Desktop.Model.ConsoleApp]* — cсылка на консольное приложение.
1. **Смещение X** *[Int32]* — cмещение по оси X. По умолчанию `10`.
1. **Смещение Y** *[Int32]* — cмещение по оси Y. По умолчанию `10`.
1. **Смещение по высоте** *[Int32]* — cмещение высоты диапазона. По умолчанию `0`.
1. **Смещение по ширине** *[Int32]* — cмещение ширины диапазона. По умолчанию `0`.
1. **Шаги** *[Int32]* — количество шагов для выделения фрагмента. По умолчанию `2`.

**Процесс**

1. **Горячая клавиша** — горячая клавиша для отправки текста в буфер обмена. Доступные значения:
   * `Ctrl Ins`— значение по умолчанию.
   * `Ctrl C`
   * `Enter`
   * `Escape`
   * `None`— клавиша не задана.
1. **Режим** — режим получения консоли. Доступные значения:
   * `Mouse` — значение по умолчанию. В этом режиме элемент **Прочитать консоль** взаимодействует с элементами консольного приложения, эмулируя действия мыши. Робот может выделить текст, щелкнуть по определенной области или выполнить другие действия, аналогичные тем, которые могли бы быть выполнены с помощью физической мыши. Этот режим обычно применяется, когда необходимо точно указать местоположение, которое не может быть достигнуто через текстовое взаимодействие.
   * `Hot Key` — в этом режиме элемент **Прочитать консоль** использует сочетания клавиш для взаимодействия с консольным приложением. Например, робот может нажимать определенные комбинации клавиш, чтобы выполнить операции, которые обычно выполняются через горячие клавиши. Этот режим предпочтителен в случаях, когда важны скорость и точность действий.
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса, указывается в миллисекундах. По умолчанию `10000`.

 **Вывод**
 
* **Переменная\*** *[String]* — название переменной, в которой будет храниться полученный из консоли текст.


## Использование

Шаг 1: Указать ссылку на консоль

В свойстве "Консоль" необходимо указать ссылку на соответствующее консольное приложение.

Шаг 2: Настройка смещений

Задать значения смещений по осям X и Y, а также ширине и высоте диапазона, если требуется.

Шаг 3: Задать количество шагов

Указать количество шагов для выделения фрагмента.

Шаг 4: Указать переменную

Введите имя переменной, в которой будет сохранен полученный текст.

Шаг 5: Настроить горячую клавишу

Если необходимо, задайте горячую клавишу для отправки текста в буфер обмена.

Шаг 6: Выбрать режим получения консоли

Выбрать  необходимый режим.

Шаг 7: Задать таймаут

Указать предельное время ожидания завершения процесса в миллисекундах.



