# Primo RPA Studio Windows 1.25.1.4


Данный раздел содержит описание изменений в **Primo RPA Studio Windows 1.25.1.4**, выпущенной в апреле 2025

📌 Рекомендация: Перед переходом на версии 1.25.\* создавайте резервные копии проектов, так как формат файлов может быть несовместим со старыми версиями Студии/Роботов.

## Улучшения Primo RPA Studio

1. В малом редакторе шаблона добавлена кнопка **Строгий поиск**. Теперь при построении дерева через пикер можно включить режим строгого поиска, аналогично основному редактору шаблона. Этот режим учитывается при валидации и построении индексов. Доступнов в режиме _Рабочий стол_.

![](<../../../.gitbook/assets1/strict_search_editor.png>)


## Улучшения Primo RPA Robot Runner

1. Добавлено интерактивное окно уведомления в **Primo RPA Robot Runner**. При запуске задачи с помощью раннера теперь появляется интерактивное окно уведомления, где пользователи могут остановить процесс, используя соответствующую кнопку `Стоп`.

![](<../../../.gitbook/assets1/robot_runner_stop.png>)

1. Реализована проверка прав при запуске локальных проектов через Robot Runner с ролью `robotraunnerlimited`. Теперь при попытке запуска локального проекта будет отображаться предупреждение, запрашивающее подтверждение действия.
1. Произведена оптимизация системы, устраняющая деградацию производительности при работе с большими процессами.

## Исправленные ошибки в Primo RPA Studio

1. Исправлена ошибка, из-за которой в большом редакторе шаблона не обновлялся отредактированный слой при добавлении или удалении нестандартного параметра селектора. Теперь внесённые изменения сразу отображаются в окне **Путь до элемента**.
1. Исправлена проблема с отображением текста в окне **Путь до элемента**: теперь текст параметров селектора корректно расширяется в соответствии с размером окна.
1. Исправлена ошибка отображения комбобокса в категории «Контейнер» в большом редакторе шаблона. Также доработана логика сохранения выбранного контейнера при перемещении элемента между контейнерами и за их пределами.
1. Исправлена ошибка, при которой в малом редакторе шаблона при выборе элемента пикером отображался лишний параметр `.text`
1. Исправлена ошибка валидации активности **Выполнить скрипт VB**, из-за которой появлялось предупреждение *"Вызывающий поток не может получить доступ к данному объекту..."*. Теперь при указании пути к файлу предупреждение от валидатора отсутствует.
1. Исправлена ошибка в элементе **Эмуляция ввода текста (WFTypeSimulate)**. Теперь активность корректно работает в браузерах и десктопных приложениях при использовании **старого ядра (v1)** (чекбокс **"Новое ядро"** в свойствах неактивен).

   - **Асинхронный режим (чекбокс "Асинхронный" в свойствах) работает только с новым ядром (v2).**
   - Если включить **"Асинхронный"**, но оставить **"Новое ядро"** выключенным, активность не будет работать.

1. Исправлена ошибка, из-за которой активность **Прокрутка** работала некорректно.
1. Исправлена ошибка, из-за которой процесс зависал при отладке, если в кастомной библиотеке присутствовал элемент **Throw**. Теперь выполнение корректно переходит в блок **Catch**, и процесс не зависает.
1. В активности **Вход в систему** устранена ошибка автоматического определения заголовка окна в браузере Chrome. Ранее в некоторых случаях требовался ручной ввод заголовка.
1. В активности **Выбрать элемент** (раздел "Работа с UI") исправлена ошибка отображения значений в выпадающем списке.
1. Исправлена ошибка, из-за которой активность **Записать формулу в ячейку** не работала с драйвером **Interop**. Теперь запись формулы в диапазон ячеек выполняется корректно.
1. Исправлена работа функции **В глубину** в диаграмме. Теперь при её выключении отладка корректно выполняется на текущем уровне, без проваливания вглубь подпроцессов.
1. Исправлена ошибка, из-за которой робот зависал при наличии двух ссылок на один и тот же процесс в последовательности, часто после выполнения блоков **Finally** и **End TryCatchCache**. Теперь процесс завершается корректно без зависаний.
1. Исправлена ошибка, из-за которой записи в консоли дублировались при повторном нажатии кнопок *Запустить процесс* или *Отладить процесс*.
1. Исправления в валидации синтаксиса (Actipro):

   - Устранены ложные предупреждения при передаче методов в *SequenceLink*
   - Исправлены ошибки проверки синтаксиса, вызывавшие некорректные сообщения

1. Устранена ошибка валидации **`Nullable<T>`**, из-за которой при использовании переменных появлялось предупреждение о некорректном синтаксисе.
1. Исправлена ошибка, из-за которой в браузерном редакторе шаблона нельзя было создать новый родительский селектор для самого верхнего уровня.
1. Исправлена ошибка при раскомментировании нескольких активностей — теперь при выборе нескольких элементов и нажатии **Раскомментировать** все выбранные активности корректно раскомментируются.
1. Исправлена ошибка выгрузки файлов зависимостей при запуске робота.
1. Устранена ошибка, из-за которой Студия прекращала работу при открытии дерева элементов в редакторе шаблона при использовании **MSAA** в активности **Присоединиться к приложению**.
1. Исправлена ошибка, из-за которой робот зависал при возникновении исключения в подпроцессе, вызванном из процесса **Чистого кода**. Теперь процесс и отладка завершаются корректно, без зависаний.
1. Исправлена ошибка, из-за которой Студия переставала отвечать при открытии старого редактора шаблона в элементе **Перетаскивание**. Теперь редактор открывается корректно.
1. Устранено дублирование пункта **Recent** в меню **File** при последовательном открытии проектов.

## Исправленные ошибки Primo RPA Robot Runner

1. Исправлена ошибка, из-за которой Robot Runner не запускал проекты **Citizen**. Теперь проекты корректно запускаются через раннер.

### Актуализация расширения браузера

✅ Для корректной работы данной версии Студии требуется обновление расширения браузера до версии **3.80 (1.80)**

## Где найти

[_Скачать версию Primo RPA Studio Windows 1.25.1.4_](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FLTS%2FStudio%2F1.25.1)

[_Скачать версию Primo RPA Robot Windows 1.25.1.4_](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FLTS%2FRobot%2F1.25.1).

Если у вас возникнут сложности с установкой или использованием данной версии, пожалуйста, обращайтесь к вашему менеджеру или в [наш чат поддержки в Telegram](https://t.me/primo_RPA_chat).
