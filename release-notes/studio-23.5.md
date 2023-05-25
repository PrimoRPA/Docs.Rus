# Primo Studio 23.5

Примечания к выпуску Студии 23.5 описывают изменения для версии приложения, выпущенной в мае 2023 года.


БРАУЗЕР! (ДИМА)


## Новые функции 

1. Баг или фича? - Элементы **Цикл ForEach** и **Цикл ForEach для DataTable** стали импортироваться с включенным параметром кеширования. Ранее при импорте для них отсутствовала галочка в свойстве **Кешировать**, хотя фактически оно производилось. Кеширование позволяет запоминать вычисляемые значения в цикле Foreach и, таким образом, выполнять проект быстрее.  https://dev.azure.com/primorpa/Primo/_queries/edit/813/?triage=true


2. В исключение добавить поле Exception.Data(словарь) для передачи значений https://dev.azure.com/primorpa/Primo/_queries/edit/1029/?triage=true


3. Условие doWhile сверху активности https://dev.azure.com/primorpa/Primo/_queries/edit/1416/?triage=true


4. Новое лого https://dev.azure.com/primorpa/Primo/_queries/edit/1981/?triage=true


5. Новое лого + фавикон https://dev.azure.com/primorpa/Primo/_queries/edit/1982/?triage=true


6. Доработка формы загрузки пакетов https://dev.azure.com/primorpa/Primo/_queries/edit/2041/?triage=true


7. Некорректное отображение отступов в элементах управление TreeView https://dev.azure.com/primorpa/Primo/_queries/edit/2205/?triage=true




## Исправленные ошибки
1. Устранено накопление данных в `C:\Users\<user>\AppData\Local\Temp\Primo.Studio`. Ранее при каждом запуске проекта с зависимостями (`.Dependencies`) из Студии или Robot Runner они копировались в папку `Temp` и не очищались. Теперь данные очищаются перед каждым запуском робота. 
1. Инструмент [пропустить элемент](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#propusk-elementa) работал не только при отладке, но и при запуске проекта, что являлось некорректным поведением. Ошибка исправлена, пропускать элемент возможно только в режиме отладки.
1. Улучшена работа окна редактора кода (Expression Editor): 
   * При закрытии Студии сбрасывалось положение окна редактора и установленный размер. Теперь настроенные параметры окна сохраняются и после завершения работы Студии.
   * Терялся фокус курсора при выборе значения из списка подсказок при написании кода - курсор через некоторое время возвращался на первую строку. Ошибка исправлена.
1. При поиске (`Ctrl` + `F`) переменных не отображались результаты из элемента **Множественное присвоение**. Ошибка была связана с тем, что не учитывались значения из свойств, представляющих собой коллекцию. Алгоритм поиска улучшен: теперь при поиске переменной также показывается, что она содержится во **Множественном присвоении**.
1. Исправлена ошибка, связанная с невозможностью очистить индекс в шаблоне поиска для браузерных приложений. Индекс стал очищаться.
1. В разделе **О программе** не отображался срок истечения оркестраторной лицензии Студии. Ошибка исправлена.
1. Исправлена ошибка, которая возникала при создании второго и последующих проектов с использованием клавиши `Enter`. Сохранить такой проект не удавалось. Теперь сохранение проектов клавишей `Enter` работает корректно.
1. Для переменных и аргументов отсутствовала проверка синтаксиса на предмет доступности ссылок на модули в DataType. Если при добавлении в проект зависимости были созданы переменные/аргументы, которые ссылались на доступный в рамках этой зависимости тип данных, то при удалении зависимости для них не отображались индикаторы ошибки :warning:. Проверка синтаксиса улучшена, теперь индикатор ошибки и ее текст отображаются.

4. Некорректное отображение функции "Отобразить компонент" https://dev.azure.com/primorpa/Primo/_queries/edit/912/?triage=true


8. Сохранение скринов активностей при перемещении "Move to new sequence" https://dev.azure.com/primorpa/Primo/_queries/edit/1036/?triage=true
9. При использовании драйвера Interop происходит некорректный ввод формулы в ячейку Excel [1207] https://dev.azure.com/primorpa/Primo/_queries/edit/1077/?triage=true
10. (1246) - Бесконечный запуск процессов при неуказанных входных аргументах https://dev.azure.com/primorpa/Primo/_queries/edit/1123/?triage=true
11. Активность "Найти начальную/конечную строку" возвращает неверные значения https://dev.azure.com/primorpa/Primo/_queries/edit/1255/?triage=true
12. Медленное выполнение процесса https://dev.azure.com/primorpa/Primo/_queries/edit/1291/?triage=true
13. Робот завис при выполнении проекта https://dev.azure.com/primorpa/Primo/_queries/edit/1329/?triage=true
14. Не работает добавление строки Таблица\"Добавить строку" через DataRow https://dev.azure.com/primorpa/Primo/_queries/edit/1344/?triage=true
15. Ширина диаграммы Excel ссылается на высоту, а высота на ширину https://dev.azure.com/primorpa/Primo/_queries/edit/1349/?triage=true
16. Баг в работе Try Catch https://dev.azure.com/primorpa/Primo/_queries/edit/1398/?triage=true
17. OpenBrowser CloseBrowser "Object reference not set to an instance of an object" в версии ядра v2 https://dev.azure.com/primorpa/Primo/_queries/edit/1484/?triage=true
18. Astro bugfix https://dev.azure.com/primorpa/Primo/_queries/edit/1594/?triage=true
19. Поддержка аргументов в активности "Запустить VBA" https://dev.azure.com/primorpa/Primo/_queries/edit/1819/?triage=true
20. Теряется связь с удаленным репозиторием https://dev.azure.com/primorpa/Primo/_queries/edit/1870/?triage=true
21. "Приостанавливать отладку на исключении" начинает отладку на исключении при обычном запуске проекта без отладки https://dev.azure.com/primorpa/Primo/_queries/edit/2001/?triage=true
22. Чтение почты - Ссылка на объект не указывает на экземпляр объекта. https://dev.azure.com/primorpa/Primo/_queries/edit/2005/?triage=true



