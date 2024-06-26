# Черный/Белый список Студий

Ч-Б список Студий - возможность создавать правила, которые определяют, какие машины имеют разрешение использовать лицензии Студии (Белый список) и каким машинам запрещено использовать их (Черный список).

**Функциональные возможности:**

1. **Создание и редактирование правил:** Только администратор системы имеет права на создание и редактирование правил в разделе **Черный/Белый список Студий**.

2. **Приоритет Белого списка:** Белый список имеет приоритет над черным. Это означает, что если машина включена как разрешенная в белом списке, она сможет использовать лицензии Студии, даже если она также включена в черный список.

**Процесс создания правила:**

1. Перейдите в раздел **Настройки** в Оркестраторе.
2. Нажмите на кнопку **Ч-Б список Студий** и выберите **Добавить правило**.

   ![](../../.gitbook/assets1/black-white_list.png)

   
3. Заполните форму настроек:
   - **Tenant:** Выберите тенант, к которому относятся учетные записи машин Студий.
   - **Параметры правила:** Вы можете настроить фильтрацию по диапазону IP-адресов машин. Укажите начало и конец диапазона IP-адресов.
   - **Маска подсети:** Введите IP-адрес подсети и ее маску. Оба значения обязательны.
   - **Разрешено (переключатель):** Определите, разрешено ли машинам использовать лицензии Студии. По умолчанию, это значение выключено, что означает, что машина будет добавлена в черный список.
   - **Наименование:** Название правила должно состоять только из букв и цифр, дефиса и подчеркивания. Пробелы недопустимы.
   - **Описание (опционально):** Добавьте небольшое описание правила, которое поможет быстрее понять его назначение при просмотре в общем списке.
4. Нажмите **Сохранить**, чтобы создать новое правило.
   

   ![](../../.gitbook/assets1/edit_black_white_list.png)
