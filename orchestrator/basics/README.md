# Сценарии работы основного пользователя

Для запуска RPA-проекта необходимо:

1. Добавить в Оркестратор RPA-проект или его версию (если не добавлен ранее).
2. Развернуть Робота на машине Робота (если не был развернут администратором).

## Добавление RPA-проекта 

Добавление проекта осуществляется на вкладке **RPA-проекты ➝ Все RPA-проекты** при нажатии на кнопку **Добавить RPA-проект**:

![](../../.gitbook/assets/0)

Здесь же можно добавить версию RPA-проекта. Для этого выделите существующий проект и используйте кнопку **Добавить версию**. 

Если RPA-проект может выполняться только Роботами определенных версий, необходимо привязать эти версии дистрибутива к RPA-проекту в поле **Версии дистрибутива робота**.

## Развертывание Робота

Развернуть Робота на машине Робота может как основной пользователь, так и администратор Оркестратора при общей настройке приложения. 

Чтобы развернуть Робота, перейдите в раздел **Роботы ➝ Все роботы** и нажмите кнопку **Добавить робота** или **Добавить роботов**:

![](<../../.gitbook/assets/1 (4)>)

Кнопка **Переразвернуть роботов** позволяет переразвернуть ранее добавленных Роботов. Сделать это можно и другим способом: сначала стереть Робота на машине (кнопка **Стереть робота (на машине)**): 

![](<../../.gitbook/assets/2 (2)>)

И затем развернуть заново (кнопки **Развернуть** или **Развернуть с параметрами**):

![](<../../.gitbook/assets/3 (1)>)

При развертывании используется [дистрибутив Робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/upload-robot). При запуске развертывания в столбце **Статус развертывания** отображается трекинг выполнения процесса:

![](../../.gitbook/assets/4)

Если трекинг не появился (индикатор в вертикальными цветными полосками), значит Оркестратор развернут неправильно, и/или неправильно настроена машина Робота. В этом случае надо обратиться к системному администратору, выполнявшему развертывание Оркестратора и настройку машины.

Развертывание завершается переходом статуса в **Готово**. Это значит, Робот удачно развернулся и готов к использованию:

![](../../.gitbook/assets/5)

Описание стадий развертывания Робота (трекинга) приведено в [Приложении 1 – Стадии развертывания Робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/appendix/appendix1). В UI Оркестратора описание стадии можно увидеть, если навести на полоску трекинга мышкой.

Например, если на какой-то стадии произошел сбой, она отображается красным, а при наведении мышкой выводится сообщение об ошибке.
