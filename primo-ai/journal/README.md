# Журнал

Для просмотра событий в Primo RPA AI Server предназначен раздел **Журнал**. Список всех существующих событий и их постоянных кодов можно просмотреть [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/journal/events).

В верхней части страницы расположены фильтры:
* **Дата события** — период, за который нужно отобразить список событий. По умолчанию значение устанавливается для текущего часа.
* **Тип события** — тип событий, который вы хотите отобразить. Нажмите выпадающий список, чтобы выбрать доступный тип события.
* **Код операции** — код операции используется, если требуется объединить несколько событий одной и той же операции и вывести их в таблице. Например, при запуске процесса генерируется уникальный код операции, который «живет» с процессом и далее — до следующего запуска процесса. Если найти событие запуска процесса, можно отфильтровать журнал по коду операции и увидеть весь жизненный цикл процесса инференс (запуск, стадии запуска, получение сигнала к остановке и т.д.). 
* **Пользователь** — логин владельца события. Текстовое поле, значение заполняется вручную.  

![Страница Журнал](<../../.gitbook/assets1/primo-ai/user-guide/monitoring.png>)

Таблица со списком событий содержит следующие поля:
1. **Событие** — название события. 
1. **IP** — IP-адрес машины владельца события.
1. **Тенант** — тенант, к которому относится событие. Если это тенант по умолчанию, то значение будет отсутствовать.
1. **Дата создания** — дата и время создания события.
1. **Пользователь** — владелец события.
1. **Text** — любая произвольная информация от разработчика, связанная с событием.
1. **EntityData** — расширенная информация о событии, например, сведения об объекте изменений. Информация в этом поле зависит от типа события и может различаться.

## Детальная информация о событии

Дополнительную информацию о событии можно просмотреть, развернув событие. 

![Иконка для показа развернутой информации о событии](<../../.gitbook/assets1/primo-ai/user-guide/events-details.png>)

Пример такой информации:
```
id:"716afd7f-80c5-4d64-a664-e8694129a12c"
event:2001
entityData:"logs, tenantId="
userId:null
apiCreatedAt:"2024-08-31T23:35:58.29378"
createdAt:"2024-08-31T23:35:58.29378"
signature:"a723bb110eceddd6e200007686b770026d2a36b3d72b189760358b0e6993d0bc"
text:null
ip:"10.0.0.24"
tenantId:null
nodeId:null
operationKey:null
classifiedEvent:3
validSignature:true
eventName:"Login"
index:1
```

В зависимости от типа события значения некоторых параметров может отсутствовать (`null`). 

В общем случае фиксируются:
* **id** — автоматически идентификатор события.
* **event** — код события. У каждого события есть свой постоянный код. Например, у события `Login` (Пользователь авторизовался) постоянный код `2001`. Он отобразится в данном поле.
* **entityData** — расширенная информация о событии. Сведения в этом поле зависят от типа события и могут различаться. Например, для события `Login` (Пользователь авторизовался) поле будет содержать информацию о тенанте пользователя и имени авторизованного пользователя. В примере выше был авторизован пользователь `logs` — [служебная учетные запись](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/admin/system-users#sluzhby).
* **userId** — логин пользователя, который является владельцем события. Для события `Login` (Пользователь авторизовался) значение отсутствует, поскольку пользователя как такового еще нет, есть только его реквизиты. Когда пользователю отдадут сессию, и этот пользователь снова обратится в сервис в рамках своей сессии, например, выполнит какую-то операцию, то его логин уже будет зафиксирован в userId.
* **apiCreatedAt** — когда был зафиксирован прием события по времени Primo RPA AI Server.
* **signature** — кодированная криптографическим алгоритмом подпись, созданная на основе данных записи журнала и секрета. Позволяет однозначно определить, что запись журнала сгенерирована системой.
* **text** — в этом поле может быть любая произвольная информация от разработчика, связанная с событием. Чаще всего присутствует при ошибках.
* **ip** — IP-адрес машины владельца события.
* **tenantId** — идентификатор тенанта, в котором произошло событие. Тенант, используемый по умолчанию, не указывается.
* **nodeId** — идентификатор ноды кластера, на которой произошло событие.
* **operationKey** — код бизнес-операции. Операция – это поток событий в рамках одного логического блока.
* **classifiedEvent** — общий тип события: информация (1), ошибка (2), инцидент безопасности (3) или корректировка (4).
* **validSignature** — флаг, принимающий значение `true`, если подпись прошла проверку компонентом Logs API сервиса.
* **eventName** — название события.
* **index** — индекс события в текущем представлении журнала.



