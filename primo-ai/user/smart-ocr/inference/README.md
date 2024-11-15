# Инференс

Инференс — использование обученной модели для предсказания на новых данных. Инференс возможен только после того, как обучение модели успешно завершилось. Машина, на которой планируется выполнить инференс, должна быть подготовлена: иметь запущенный агент и файл обученной модели.

Подготовка целевой машины для инференса — задача пользователя Primo RPA AI Server на данном этапе. Настройка состоит из нескольких последовательных действий:
1. Создание шаблона процесса инференса.
2. Создание процесса инференса.
3. Запуск процесса инференса на целевой машине.

Все действия осуществляются на странице **Инференс**.

![](<../../../../.gitbook/assets1/primo-ai//user-guide/inference-page.png>)

## Содержание

* [Как запустить процесс инференса](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/user/inference/run-inference-process)

## Что дальше

После того, как на целевой машине успешно запущен инференс, работа с проектом в Primo RPA AI Server может быть завершена. Следующий шаг — подготовить RPA-проект в Primo RPA Studio, который будет взаимодействовать с Primo RPA AI Server и вашей подготовленной целевой машиной. 

Для разработки RPA-проекта понадобится установить библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server) в Primo RPA Studio.

:large_blue_diamond:***Примечание**. Изображения для инференса добавляются в рамках RPA-проекта, в веб-интерфейсе Primo RPA AI Server эта функция отсутствует.*