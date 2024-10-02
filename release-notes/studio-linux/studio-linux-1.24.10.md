# Primo RPA Studio Linux 1.24.10

Раздел содержит описание изменений для версии приложения **Primo RPA Studio Linux 1.24.10**, выпущенной в октябре 2024 года. 

## Новые функции и улучшения

1.	Добавлена поддержка браузерного расширения Хром 3.68 с манифестом v3.  
2. Обновлена текущая версия браузерного расширения Хром с манифестом v2 до 1.68.
3. Добавлены следующие активности группы **Браузер**:
* Открыть вкладку браузера
* Активировать вкладку браузера
* Активная вкладка
* Закрыть вкладку браузера
4. В консоль добавлена возможность показа времени вывода логов до мс включительно.
5. Добавлено контекстное меню для редактора чистого кода.
6. В группу **Работа с UI** добавлена активность *Клик мышью*.
7. В группу **Рабочий стол** добавлена активность *Выбор элемента*.
8. Добавлена возможность использовать активность **Управление: Ссылка на процесс** в скриптах и процессах типа Чистый код.

## Исправленные ошибки 

1.	Описание элемента **Данные: Таблицы данных: Удалить повторяющиеся строки** приведено в соответствие с названием элемента.
1.	Исправлена некорректная работа кнопки **Пропуск элемента**, из-за которой при создании проекта и добавлении множества элементов первый элемент в этой последовательности не пропускался, несмотря на нажатую кнопку.
1.	Восстановлена работоспособность элемента **Рабочий стол: Присутствие элемента**.
1.	Устранена ошибка, из-за которой при работе в отладке с вложенными процессами дважды открывался вызываемый процесс или выдавалось сообщение об ошибке "Control already has a visual parent". 
1.	Исправлена ошибка в работе контейнера **Браузер: Якорь**, приводившая к игнорированию свойства якоря «Расположение» для элементов *Выбор значения, Выбрать элемент, Фокус ввода, Получение списка*.
1.	Решена проблема с зависанием отладки процесса в случае попытки «Сделать шаг» (при этом становились неактивными кнопки «Сделать шаг» и «Возобновить процесс»).
1.	Исправлены проблемы с кодировкой в почтовых активностях, из-за которых при попытке чтения писем возвращались нечитаемые символы.
1.	Откорректирован тип переменной, предлагаемой по умолчанию по комбинации клавиш «ctrl+k» при создании переменной-индекса в активностях группы **Управление** -   *Цикл ForEach, Цикл ForEach для DataTable, Повтор N раз*. Теперь тип данных – Int32.
1.	Исправлена ошибка, из-за которой не появлялось окно сохранения проекта при закрытии Студии или открытии другого проекта, что приводило к невозможности сохранить проект.
1.	Устранены проблемы в работе активности **OCR: Поиск изображения**, связанные с работой с координатами, а также с появлением исключения при снятом флажке «Throw exception». 
1.	Исправлена ошибка в работе инструмента **Поиск в закрытых** (*Проект -> Найти -> Поиск в закрытых*) – при которой в только что открытой Студии не открывалась панель свойств у элементов, если был использован данный инструмент.
1.	Решена проблема, из-за которой при попытке открытия процесс перемещался по открытым каталогам проекта. 
1.	Восстановлена работа панели **Наблюдение**: панель корректно отображает значения переменных, за которыми ведется Наблюдение.

## Где найти 

[Скачать дистрибутив Primo RPA Studio Linux](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FStudio)

[Скачать дистрибутив Primo RPA Robot](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FRobot)