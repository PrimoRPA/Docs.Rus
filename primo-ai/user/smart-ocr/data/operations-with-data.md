# Управление данными

Пользователь может добавить изображения в проект, просмотреть, редактировать, повернуть и удалить. 

Поддерживается несколько способов добавления изображений:
* [добавление отдельными файлами](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/user/smart-ocr/data/operations-with-data#dobavit-izobrazheniya);
* [добавление архивом](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/user/smart-ocr/data/operations-with-data#dobavit-izobrazheniya-arkhivom);
* [импорт существующего датасета вместе со схемой разметки](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/user/smart-ocr/data/operations-with-data#import-dataseta).

## Добавить изображения

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь права «Проект — Просмотр, Создание».*

1. Изучите [требования к формату и качеству изображений](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/user/smart-ocr/requirements/inference-quality-requirements).
1. Находясь в выбранном проекте, перейдите на страницу **Данные**.

   ![Страница «Данные»](<../../../../.gitbook/assets1/primo-ai/user-guide/data-in-project.png>)

1. Нажмите кнопку **Добавить изображения** — откроется форма для загрузки изображений.

   ![Форма для загрузки файлов](<../../../../.gitbook/assets1/primo-ai/user-guide/add-data-files.png>)

1. Выберите со своего диска все изображения, которые хотите добавить.
1. Нажмите **Сохранить**.


## Добавить изображения архивом

1. Изучите [требования к формату и качеству изображений](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/user/smart-ocr/requirements/inference-quality-requirements).
1. Перейдите на страницу **Данные** и нажмите кнопку **Загрузить архив**.

   ![Кнопка «Загрузить архив»](<../../../../.gitbook/assets1/primo-ai/user-guide/data-button-addarchive.png>)

1. Перетащите в область загрузки ZIP-архив с изображениями для обучения.

   ![Форма загрузки архива](<../../../../.gitbook/assets1/primo-ai/user-guide/dataset-import-form.png>)

1. Нажмите **Сохранить**.

Добавленный архив автоматически распакуется через несколько секунд. Увидеть все архивы проекта можно по кнопке **Архивы**.

На странице с архивами отображается статус каждого архива. Когда изображения будут автоматически извлечены, архив будет иметь статус `Загружен`. После чего изображения отобразятся в табличной части страницы **Данные**.

![Страница «Архивы»](<../../../../.gitbook/assets1/primo-ai/user-guide/data-archives-list.png>)


## Импорт датасета

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь права «Проект — Просмотр, Создание».*

Архив, который вы хотите импортировать, предварительно должен быть скачан из другого проекта. В таком архиве присутствуют размеченные изображения и готовая схема разметки.

Если в вашем проекте уже существует схема разметки, которая отличается от импортируемой, то при распаковке архива будет автоматически создана новая схема разметки. Чтобы этого не произошло, перед импортом датасета убедитесь, что ваша схема разметки полностью совпадает с импортируемой: имеет одинаковое количество полей и названия полей. 

1. Перейдите на страницу **Данные** и нажмите кнопку **Импорт датасета**.

   ![Кнопка «Импорт датасета»](<../../../../.gitbook/assets1/primo-ai/user-guide/dataset-import-button.png>)

1. Перетащите в область загрузки ZIP-архив с датасетом.

   ![Форма загрузки архива с датасетом](<../../../../.gitbook/assets1/primo-ai/user-guide/dataset-import-form.png>)
   
1. Нажмите **Сохранить**.


## Просмотреть изображения

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь право «Проект — Просмотр».*

Все добавленные изображения для обучения модели отобразятся в табличной части страницы **Данные**.

![Таблица данных](<../../../../.gitbook/assets1/primo-ai/user-guide/data-table.png>)

Таблица имеет следующие поля:
1. **Миниатюра** — уменьшенная копия изображения.
2. **Название файла**.
3. **FileSize** — размер файла.
4. **Format** — формат файла.
5. **Описание** — описание изображения. Пользователь может добавить описание при редактировании изображения, иначе оно будет пустым.
6. **Автор** — логин пользователя, загрузившего изображение.
7. **Дата создания** — дата добавления изображения.
8. **Действия** — список доступных действий с изображением.


## Редактировать изображение
:large_blue_diamond:***Примечание**. Роль пользователя должна иметь права «Проект — Просмотр, Редактирование».*

1. Находясь в выбранном проекте, перейдите на страницу **Данные**.
1. В таблице данных найдите нужную запись и нажмите значок ☰ для вызова меню действий.
1. Выберите **Редактировать**. На данный момент редактирование позволяет только добавить описание к изображению.
1. Добавьте описание и выберите **Сохранить**.

![Форма редактирования изображения](<../../../../.gitbook/assets1/primo-ai/user-guide/edit-datafile-form.png>)


## Повернуть изображение

:large_blue_diamond:***Примечание**. Роль пользователя должна иметь права «Проект — Просмотр, Редактирование».*

1. Находясь в выбранном проекте, перейдите на страницу **Данные**.
1. В таблице данных найдите нужную запись и нажмите значок ☰ для вызова меню действий.
1. Выберите действие **Повернуть**.

   ![Вызов действий](<../../../../.gitbook/assets1/primo-ai/user-guide/button-rotate-image-datapage.png>)
   
1. Откроется форма с изображением для редактирования:
   * 1 — кнопки поворота изображения на 90 градусов по часовой стрелке или против часовой стрелки.
   * 2 — переключатель сетки. Сетка представляет собой непечатаемые линии и помогает симметрично расположить изображение. Если переключатель переведен вправо, сетка включена. Если влево — сетка скрыта.
   * 3 — кнопки для управления масштабом изображения. Масштаб также можно изменять колесиком мыши.
   * 4 — поворот изображения на указанный вами угол.
  
   ![Рабочая область для поворота изображения](<../../../../.gitbook/assets1/primo-ai/user-guide/rotate-image-page.png>)


## Удалить изображение
:large_blue_diamond:***Примечание**. Роль пользователя должна иметь права «Проект — Просмотр, Удаление».*

1. Находясь в выбранном проекте, перейдите на страницу **Данные**.
1. В таблице данных найдите нужную запись и нажмите значок ☰ для вызова меню действий.
1. Выберите действие **Удалить** и подтвердите его.
