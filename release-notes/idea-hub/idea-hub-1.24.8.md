# Idea Hub 1.24.8

Список изменений в Primo RPA Idea Hub, которые вошли в версию 1.24.8. 

## Обновления и улучшения

1. Для числовых полей появилась настройка, которая позволяет управлять отображением значений. Теперь вы можете установить конкретное число, начиная от которого значения необходимо автоматически сворачивать. Ранее значения автоматически сворачивалась, если сумма в поле была больше миллиона. Благодаря новой функции, вы можете снизить этот порог.   https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25747

1. Добавлена возможность управлять доступом к каждому полю процесса (только процесса или всех материалов?). **Для этого в правах доступа роли появился блок разрешений Field (Верно?). Какие разрешения появились, подробнее расписать, как настраиваются** https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25778

   

1. Реализовать связь между материалом типа Очередь с соответствующей статистикой в хранилище  https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25887

1. Реализовать связь между материалом типа Проект с соответствующей статистикой в хранилище  https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25886

1. Из типа материала Очередь удалить поля, в которых хранили статистику https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25884

1. Добавить возможность управлять "дельтами" https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25146

1. Реализовать возможность создания произвольные типы комплексных полей https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25749

1. Добавить новое рассчитываемое поле https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25138

1. Добавить новую пользовательскую функцию  (что за функция?) https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25135

1. Добавить возможность управлять разделителями баджей в краткой версии карточек процессов https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25180

1. Добавить в представления "No result" https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25375

1. Перенести список департаментов из демо inner https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25396

1. Исправить правила обновления сервера staging https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/26557

1. Сохранять получаемые из текущего оркестратора данные в новое датированное хранилище https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25121

1. Перенести добавление t() в stagin для доступных значений поля "Период операций"  https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25127

1. Организация хранения обязательных датированных данных от системы RPA   https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25061

1. Перенести функциональность миграции RateAndHumanDuration в модуль поля PrimoComplex https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/20670


## Исправленные ошибки

1. Исправлена ошибка, из-за которой не обновлялась иконка пользователя в меню. Ранее иконка корректно обновлялась только у администратора. https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25750
1. Исправлена ошибка в миграции, из-за которой департаменты не обновлялись корректно. https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25748
1. ПОЯСНИТЬ (ЧТО ТАКОЕ ТИЗЕР, КАКИЕ ДИСПЛЕИ ИМЕЮТСЯ В ВИДУ) Исправлена ошибка, из-за которой нельзя было изменить иконки в тизере. Теперь в любом дисплее можно настроить иконки для полей процесса.  https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/24291
1. Исправлена ошибка, из-за которой экспорт процессов завершался ошибкой при отсутствии департамента, привязанного к процессу.  https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/26209
1. Исправлена ошибка, из-за которой не работал поиск в английской версии сайта. https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/15583
1. Решена проблема, из-за которой на странице очередей не работали региональные настройки.  https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/25022

1. Ошибка при запуске крона primo_migrate_node_license_presave()->getTimestamp https://azure-dos.s1.primo1.orch/PrimoCollection/IdeaHub/_workitems/edit/23241

