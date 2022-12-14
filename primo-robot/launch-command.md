# Запуск из командной строки

Запустить Робота можно двумя способами: с помощью программы [Primo Robot Runner](https://docs.primo-rpa.ru/primo-rpa/primo-robot/robot-runner) или из командной строки.

Для старта из командной строки воспользуйтесь приложением **Primo Robot**: запустите его с помощью ярлыка на Рабочем столе или из меню **Пуск**. Программа обладает минимальным графическим интерфейсом:

![](<../../.gitbook/assets/0 (8).png>)

Кнопка ![](<../../.gitbook/assets/4 (8).png>) служит для очистки текста консоли Робота.

**ВНИМАНИЕ!** Чтобы программа работала корректно, предварительно запросите лицензию через Primo Robot Runner: процесс подробно описан [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-robot/robot-runner/registration-desktop#poluchenie-licenzionnogo-klyucha-i-registraciya).

Для запуска Робота из командной строки используйте следующие аргументы:

* **projPath:** путь к папке выполняемого проекта
* **seqPath:** путь к главной последовательности проекта
* **instantStart:** стартовать запуск проекта как только робот будет загружен
* **exitOnSuccess:** закрыть робота по завершении выполнения проекта
* **noOrchestrator:** режим работы в отсутствии оркестратора (обязателен, если робот запускается вручную)
* **StartupPosition:** вариант отображения робота на старте. Возможные варианты - Normal (стандартный), Minimized (свернутый), Maximized (во весь экран), Tray (свернут в системный трэй)
* **CloseRdp:** автоматически корректно завершать сессию RDP на старте
* **logToFile:** признак записи журнала в файл (папка Log)
* **logCustomToFile:** признак записи пользовательских событий в журнал
* **logMsgTypes:** типы журналируемых событий (Error, Info, Debug, Network). Для указания нескольких используется символ | (Error|Info|Debug)
* **logType:** тип журнала (Text, Csv)
* **noConsole:** отключает отображение журнала в консоли
* **RunConfig:** тип конфигурации запуска (для переменной WorkflowVar.RunConfig). Возможные варианты: None, Debug, Release
* **RunConfigCustom:** тип конфигурации запуска (для переменной WorkflowVar.RunConfigCustom)

Пример:

`Primo.Robot.exe instantStart exitOnSuccess noOrchestrator logType=Csv "seqPath=C:\Work\Project\Sequence.ltw" "projPath=C:\Work\Project\\`
