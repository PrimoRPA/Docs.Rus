# Студия 1.24.6

## Обновления и улучшения

1. Расширение для браузеров стало поддерживать работу с [Манифестом V3](https://developer.chrome.com/docs/extensions/develop/migrate/what-is-mv3?hl=ru) — последней версией платформы расширений Chrome Extensions. Теперь при [ручной установке расширения](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install) Primo RPA Extension вы cможете указать, какую версию Манифеста следует использовать: 2 или 3. Переход на V3 возможно осуществить в течение года, что позволяет изучить возможности обновленного расширения без ущерба для бизнес-задач.

   ![](<../.gitbook/assets1/studio/settings/Manifestv3.png>)

1. Обновлено расширение Primo RPA Extension. Новая версия расширения поддерживает взаимодействие с веб-клиентом 1С, включая возможность выбирать шаблон поиска с помощью xPath. Улучшение распространяется на обе версии Манифеста.
1. Расширены функции поиска в проекте — теперь возможно [заменить](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/search) найденную строку на заданное значение. Функция замены призвана сократить время, требуемое для внесения изменений в RPA-проект. По умолчанию замена недоступна, чтобы активировать функцию, необходимо включить в [настройках](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#obshie) Студии параметр **Найти и заменить**.
1. При запуске Robot Runner'a стал отображаться экран загрузки, сигнализирующий пользователю о том, что процесс осуществляется корректно, и нет необходимости повторно запускать приложение.
1. Для процесса с типом "Диаграмма" добавлена возможность сделать паузу во время отладки. Функция выполняет ту же роль, что приостановка отладки для других типов процессов.



## Ошибки

1. В новом редакторе шаблона исправлена валидация десктопных селекторов, работающих с типом автоматизации UIAUTOMATION. 
1. В новом редакторе шаблона исправлено сообщение о результате валидации, отображаемое при превышении таймаута поиска. 
1. В предварительном редакторе шаблона изменен цвет шрифта на вкладке "Код". Ранее, при выборе темной темы Студии, цвет кода затруднял понимание данных.
1. Исправлена ошибка в элементе **Функция BAPI**, возникавшая после нажатия кнопки Refresh в окне с функцией. 
1. Исправлена ошибка, из-за которой циклы ForEach некорректно работали с виртуальными переменными, если в цикле выполнялся вызов подпроцесса. 

