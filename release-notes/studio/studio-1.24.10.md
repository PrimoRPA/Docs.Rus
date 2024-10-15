#  Primo RPA Studio Windows  1.24.10

Изменения в **Primo RPA Studio** за октябрь 2024-го года

## Обновления и улучшения (режим Pro)

1. Добавлена возможность пакетного включения/отключения логирования элементов (для выделенных элементов).  

1. Добавлена активность [**Дочерние элементы (FindChildren)**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_find_children) для поиска дочерних элементов интерфейса. 
В элементе присутствуют параметры, которые позволяют гибко настраивать область поиска элементов. Для использования данной функции может потребоваться обновление расширения браузера до версии 3.71(1.71)

1. В панели **Наблюдение (Watch)** теперь поддерживается выполнение C# кода, что дает разработчикам возможность тестировать код и работать с переменными в памяти без необходимости полного запуска проекта.

**1. Добавлена возможность авторизации в Оркестраторе с использованием Windows-учетной записи. Для выполнения действий, связанных с Оркестратором (через AD-авторизацию), необходимо добавлять группы Active Directory (AD) в встроенные системные роли, такие как Robot или Studio.**

1. В элемент Outlook **Отправить сообщение (Send message)** добавлены новые свойства: `Уведомить о доставке` и `Уведомить о прочтении`, что позволит запрашивать уведомления о доставке и прочтении отправленных писем. По умолчанию оба свойства выключены.

**1. Добавлено свойство `Аргументы запуска` в элемент **Открыть браузер**. Теперь пользователи могут передавать параметры запуска браузера напрямую.**

1. Добавлены новые свойства в элемент **Получить из очереди по фильтру**.
Теперь доступны параметры `Получать метаданные` и `Получать тэги`, позволяющие пользователям выбирать, следует ли получать эти данные при обработке очереди.

1. Улучшена работа элемента **Исключение (Throw)**: теперь он поддерживает передачу исключений не только типа `Exception`, но и типа `LTools.Common.Model.ExecutionExceptionInfo`. Это позволяет передавать одну и ту же переменную исключения из блока TryCatch в Throw, что улучшает обработку исключений.

1. Улучшен анализатор кода: переименована библиотека с новыми правилами в `Primo.ProjectAnalyzer.Extended` и добавлена инструкция в настройках анализатора для удобства использования.

1. Добавлено уточнение в текст исключений у элемента **Множественное присвоение**. Теперь в тексте исключения указывается, на каком именно присвоении произошла ошибка,с указанием его индекса.

1. Улучшено отображение интерфейса, обновлена визуализация ключевых элементов интерфейса: стартового экрана, экрана выбора режима работы и экрана загрузки (сплэш-скрина).

1. Обновлен дизайн окна **Найти и заменить**. Добавлены чекбоксы в режиме замены и предупреждения при нажатии кнопки замены.

1. Обновлены названия свойств в элементах работы с  очередями:
   - В элементе **Добавить в очередь** название свойства `Идентификатор` изменено на `Ключ` (в англоязычном интерфейсе — `Key`).
   - В элементе **Получить из очереди по фильтру** название свойства `ID` изменено на `Ключ` (в англоязычном интерфейсе — `Key`).



### Исправленные ошибки

1. Исправлена ошибка в активности **Прочитать таблицу**, при которой выбранные теги из селектора не добавлялись в шаблон, если не была установлена галка на теге `Class`. Теперь шаблон таблицы корректно формируется как с галкой на параметре `Class`, так и без нее, и работает корректно как в контейнере, так и без него.

1. Исправлена ошибка, при которой скопированный элемент исчезал из диаграммы при попытке его закомментировать. Теперь скопированный элемент в диаграмме корректно сохраняется на месте при попытке его закомментировать.

1. Исправлена ошибка автосохранения открытых процессов в файлы `.bak` по расписанию. Теперь все открытые, включая изменённые, но не сохранённые процессы, корректно сохраняются в `.bak` файлы в соответствии с установленным периодом автосохранения.

1. Исправлена ошибка, при которой активность **Получить из очереди по ID (PeekQueueById)** некорректно отображала статус элемента очереди после его изменения. Теперь статусы элементов отображаются корректно в соответствии с их актуальным состоянием.

1. Исправлено некорректное отображение списка избранных элементов.
Ранее список **Избранные** не отображался при открытии проекта до тех пор, пока не был добавлен новый элемент. Теперь список корректно подгружается сразу при открытии Студии.

1. Исправлено некорректное сохранение ID элемента в переменную у элемента **Ожидать сообщения из очереди**.
Теперь ID элемента корректно сохраняется в переменную и совпадает с отображаемым ID в Оркестраторе.

1. Исправлена ошибка, из-за которой робот не мог запустить привязанный к элементу `ComboBox JS-скрипт` при использовании элемента **Выбрать значение (Select Item)**, при этом скрипт срабатывал при ручном выборе. 
Теперь робот запускает скрипт корректно при выборе элемента.

## Robot Runner

1. Ограничен запуск более одного экземпляра **Primo Robot Runner**. Ранее возможен был запуск нескольких экземпляров, что могло приводить к ошибкам и некорректному выполнению процессов. 
1. Улучшен интерфейс Robot Runner:
  - Окно `О программе` теперь отображает версию программы, разрядность системы и содержит ссылки на документацию, академию, раздел вопросов и ответов, GitHub репозиторий и чат пользователей в Telegram.
  - Добавлены новые темы для персонализации интерфейса Robot Runner, улучшая его внешний вид и настройку под пользователя.

## Citizen 

В элементах Citizen больше не отображается значок `Пропуск элемента`. Это изменение соответствует концепции упрощённого режима работы в Citizen Studio.


## Где найти

[**Скачать Primo RPA Studio**](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FStudio)

[**Скачать Primo RPA Robot**](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FRobot). 


Если у вас возникнут сложности с установкой или использованием данной версии, пожалуйста, обращайтесь к вашему менеджеру или в [наш чат поддержки в Telegram](https://t.me/primo_RPA_chat).



