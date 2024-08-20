# Управление полями схемы

## Добавить поля в схему разметки

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь право «Схемы разметки — Создание».*

1. Перейдите на страницу **Схемы разметки** и кликните по названию схемы.
1. Нажмите кнопку **Добавить поле**
1. Укажите название поля. В названии допускаются только буквы, цифры, дефис, подчеркивания и точки.
   * *Если вы используете **модель-классификатор**, то название поля должно отражать тип документа.*
   * *Если вы используете **модель для распознавания данных в документе**, то название поля — это категория информации, которая должна быть извлечена из документа.*
1. Добавьте краткое описание поля, если необходимо.
1. Нажмите **Сохранить**.

![](<../../../../.gitbook/assets1/primo-ai/user-guide/go-to-schema-fields.gif>)

### Пример полей для модели-классификатора

Во встроенном проекте «Классификатор» модель обучена предсказывать, к какому типу документов принадлежит изображение: паспорт, СНИЛС или Торг-12.

Чтобы обучить данную модель, была создана схема разметки с полями:
1. Паспорт
2. СНИЛС
3. Торг-12.

Таким образом, каждое название поля — это класс или тип документа, который должен быть известен модели для успешного совершения предсказаний.

### Пример полей для модели распознавания

Во встроенном проекте «Паспорт» модель обучена распознавать данные по известным категориям.

Чтобы обучить данную модель, была создана схема разметки с полями:
1. Фамилия
2. Имя
3. Отчество
4. Пол
5. Дата рождения
6. ...

Таким образом, поле «Фамилия» или «Дата рождения» будет являться категорией информации, которую необходимо извлечь и структурировать для дальнейшего использования моделью распознавания данных. 


## Просмотр списка полей схемы

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь право «Схемы разметки — Просмотр».*

Все добавленные в схему поля отображаются в табличной части страницы **Поля схемы**.

![](<../../../../.gitbook/assets1/primo-ai/user-guide/scheme-fields-list.png>)

Таблица имеет следующие столбцы:
1. Название — название поля, которое задал пользователь.
2. Описание — описание поля, которое задал пользователь.
3. Тип — не используется, столбец реализован для будущих версий приложения.
4. Язык — не используется, столбец реализован для будущих версий приложения.
5. Строки — не используется, столбец реализован для будущих версий приложения.
6. Действия — доступные действия с полем схемы: редактировать, удалить.

## Редактировать поле

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь право «Схемы разметки — Редактирование».*

1. Перейдите на страницу **Поля схемы**.
1. В таблице данных найдите нужную запись и нажмите значок ☰ для вызова меню действий.

   ![](<../../../../.gitbook/assets1/primo-ai/user-guide/fields-actions.png>)

1. Выберите действие **Редактировать**.
1. Измените нужные свойства и выберите **Сохранить**.

   ![](<../../../../.gitbook/assets1/primo-ai/user-guide/edit-field-form.png>)


## Удалить поле из схемы разметки

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь право «Схемы разметки — Удаление».*

1. Перейдите на страницу **Поля схемы**.
1. В таблице данных найдите нужную запись и нажмите значок ☰ для вызова меню действий.
1. Выберите **Удалить** и подтвердите действие.