# Развертывание робота

Развернуть робота на машине робота может как основной пользователь, так и администратор Оркестратора при общей настройке приложения. 

Чтобы развернуть робота, перейдите в раздел **Роботы ➝ Все роботы** и нажмите кнопку **Добавить робота** или **Добавить роботов**:

![](<../../.gitbook/assets/1 (4)>)

При развертывании можно выбрать версию ядра робота - она влияет на скорость загрузки больших RPA-проектов. Новая версия ядра, v2, обладает улучшенной производительностью.

При развертывании используется [дистрибутив робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/robots/upload-robot). При запуске развертывания в столбце **Статус развертывания** отображается трекинг выполнения процесса:

![](../../.gitbook/assets/4)

Если трекинг не появился (индикатор в вертикальными цветными полосками), значит Оркестратор развернут неправильно, и/или неправильно настроена машина робота. В этом случае надо обратиться к системному администратору, выполнявшему развертывание Оркестратора и настройку машины.

Развертывание завершается переходом статуса в **Готово**. Это значит, робот удачно развернулся и готов к использованию:

![](../../.gitbook/assets/5)

Описание стадий развертывания робота (трекинга) приведено в [Приложении 1 – Стадии развертывания Робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/appendix/appendix1). В UI Оркестратора описание стадии можно увидеть, если навести на полоску трекинга мышкой. Например, если на какой-то стадии произошел сбой, она отображается красным, а при наведении мышкой выводится сообщение об ошибке.

Развернутых роботов можно впоследствии переразвернуть одним из этих способов:
* по кнопке **Переразвернуть роботов**; 
* сначала стереть робота на машине (кнопка **Стереть робота (на машине)**): 

![](<../../.gitbook/assets/2 (2)>)

и затем развернуть заново (кнопки **Развернуть** или **Развернуть с параметрами**):

![](<../../.gitbook/assets/3 (1)>)

При переразвертывании робота также возможно изменить версию ядра в одноименном параметре расширенных настроек. Чтобы понять, с каким ядром работает тот или иной робот, посмотрите в таблице на столбец **Наименование**: версия 2 будет отмечена после имени робота как v2, версия 1 отображаться не будет.
