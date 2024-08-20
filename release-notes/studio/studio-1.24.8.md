# Primo Studio 1.24.8

История изменений в Primo Studio для Windows за август 2024-го года. 


## Обновления и улучшения (режим Pro)

1. Добавлен новый элемент [Закрыть вкладку брузера (Close Tab)](https://github.com/PrimoRPA/Docs.Rus/issues/1477), позволяющий закрывать вкладки в браузерах (IE, Chrome, Firefox) по индексу, заголовку или переменной, полученной на уровне элементов **Open Browser (Открыть браузер)**, **Attach Browser (Присоединиться к браузеру)**, **Open Application (Открыть приложение)**, **Attach Application (Присоединиться к приложению)**. При использовании браузера Firefox с Манифестом V3 необходимо убедиться, что присутствуют нужные разрешения.
https://azure-dos.s1.primo1.orch/PrimoCollection/Studio/_workitems/edit/3702
1. Добавлено новое свойство `Сохранить изменения` в элементы **Приложение Excel** и **Приложение Word**. По умолчанию чекбокс неактивен, что позволяет избежать случайного сохранения изменений. При активации чекбокса внесенные изменения в документы будут сохранены автоматически. https://azure-dos.s1.primo1.orch/PrimoCollection/7e9b15e6-a27e-4ad1-9d22-2c3952e66adc/_workitems/edit/3261
1. Улучшено отображение шаблонов в интерфейсе Студии: теперь шаблоны отображаются на языке, выбранном в настройках интерфейса (русском или английском).
https://azure-dos.s1.primo1.orch/PrimoCollection/Studio/_workitems/edit/20598
1. Увеличено время ожидания (Timeout) для всех элементов, относящихся к разделу `Оркестратор` (очереди, процесс, ресурсы), до 30 секунд. По умолчанию значение таймаута составляет 30 000 мс, что поможет предотвратить ошибки из-за недостаточного времени выполнения.
https://azure-dos.s1.primo1.orch/PrimoCollection/Studio/_workitems/edit/147





















## Исправленные ошибки 

1. Исправлена ошибка, из-за которой при отладке процесса с типом **Диаграмма** не происходил переход внутрь элементов, несмотря на активированную опцию `В глубину`.
https://azure-dos.s1.primo1.orch/PrimoCollection/Studio/_workitems/edit/21266

1. Исправлена ошибка, возникавшая при создании библиотеки, если в проекте присутствовали переменные типа DataTable. Теперь процесс создания библиотеки выполняется корректно и без ошибок.
https://azure-dos.s1.primo1.orch/PrimoCollection/Studio/_workitems/edit/17479
@1. Исправлена ошибка `System.OutOfMemoryException`, возникающая при поиске с галочкой **Искать в закрытых** в Студии x86. Теперь поиск в закрытых ltw проектах осуществляется без возникновения ошибки.
https://azure-dos.s1.primo1.orch/PrimoCollection/Studio/_workitems/edit/15534
1. Исправлена ошибка в чистом коде при использовании оператора else в отладчике чистого кода v2. Теперь, при выполнении блока if, блок else корректно пропускается, и отладка работает без ошибок.
https://azure-dos.s1.primo1.orch/PrimoCollection/Studio/_workitems/edit/15541

## Режим Citizen



## Где найти
[Скачать дистрибутив Primo RPA Studio Enterprise](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FStudio%2FWindows).

[Скачать дистрибутив Primo RPA Robot](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FRobot%2FWindows):
* **Primo RPA Robot 1.24.6** — предназначен для установки на локальной рабочей станции. Выступает в роли цифрового ассистента пользователя. Дистрибутив поставляется в разрядности x64 и x86.