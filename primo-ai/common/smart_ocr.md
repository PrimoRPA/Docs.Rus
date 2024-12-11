# Умный OCR

Умный OCR — программный компонент AI Server, предназначенный для обработки изображений документов. Компонент содержит сверточные нейросети (Convolutional Neural Networks, CNN) — модели глубокого обучения, специально разработанные для обработки изображений. Эти модели широко используются в задачах компьютерного зрения, помогают классифицировать изображения и распознавать в них данные.

## Типы моделей в Умном OCR
Модели Умного OCR делятся на типы в зависимости от задач, которые они должны решать:
* **Модель классификации** — классифицирует документы по заранее известным типам документов.
* **Модель распознавания данных в документах утвержденной формы** — распознает данные в заранее известном типе документа и возвращает их в структурированном формате (json).
* **Модель распознавания данных в документах произвольной формы** — распознает данные в документе свободной формы и возвращает их в структурированном формате (json).

## Общий порядок работы с моделью
Процесс работы с моделью любого типа состоит из следующих этапов:
1. Обучение модели.
1. Тестирование модели.
1. Использование модели для решения конкретной задачи.

### Шаг 1. Обучение модели
Чтобы модель могла успешно выполнять поставленную задачу, ее требуется предварительно обучить. Обучение проводится на специально подготовленном наборе изображений — *датасете*. Все изображения датасета пользователю необходимо разметить — метки к данным укажут модели, объекты какого класса присутствуют на изображениях. Разметка играет ключевую роль в машинном обучении, поскольку помогает алгоритмам эффективно обучаться.

В процессе обучения модель адаптируется к особенностям конкретного датасета и минимизирует ошибку предсказания. Хорошо обученная нейросеть должна не только хорошо работать на обучающих данных, но и обобщать свои знания на новые, ранее невидимые данные.

Для этого при обучении модель корректирует свои параметры (веса), ориентируясь на разницу между предсказанными результатами и истинными метками на изображениях. Чтобы достичь высоких показателей обучения, способности модели также проверяются на тестовом датасете, что позволяет отслеживать ее производительность и вносить корректировки в процесс обучения.

**Кто может обучать модель?**

Обучать модель любого типа могут сотрудники без специальных навыков. Для этого сервис предоставляет:
* инструменты для разметки изображений и формирования датасетов;
* инструменты для обучения и мониторинга процесса обучения.


### Шаг 2. Тестирование модели

Пользователь может самостоятельно протестировать способности обученной модели до ее применения в продуктивной среде. Тестовые запросы позволяют оценить, насколько хорошо модель справляется с задачей, для которой была обучена. С помощью тестовых запросов проверяются различные сценарии использования модели с целью обнаружить потенциальные проблемы в виде низкой точности или ошибок классификации. Конечная цель тестирования — убедиться, что модель стабильно работает и не выдает неожиданных результатов.

**Как отправить тестовый запрос?**

В интерфейсе AI Server есть инструмент для отправки тестового запроса — пользователю потребуется выбрать тип модели и загрузить изображение. Результат отобразится на специальной странице, будет доступен для скачивания и копирования.


### Шаг 3. Использование модели

Под использованием модели понимается *инференс* — процесс применения обученной модели для выполнения предсказаний на новых, ранее невидимых данных. Этот этап следует за обучением модели, когда она была натренирована на специальном наборе данных и теперь готова использовать свои знания для решения реальных задач.

Кроме того, в поставке AI Server существует набор моделей, обученных и оптимизированных командой Primo RPA. Набор моделей постоянно расширяется в зависимости от версии сервиса и на текущий момент содержит:
* модель для классификации документов по типам: паспорт, СНИЛС, Торг-12;
* модель для распознавания данных в изобажениях паспортов;
* модель для распознавания данных в изобажениях СНИЛС;
* модель для распознавания данных в изобажениях Торг-12;
* модель для распознавания данных в изобажениях документа произвольной формы на белом фоне.

Перечисленные модели готовы для использования в продуктивной среде без предварительного шага в виде обучения.


**Как запустить инференс?**

AI Server содержит специальные инструменты для запуска инференса:
* централизованное управление машинами с агентами для Умного OCR;
* API для внешних систем;
* специальная библиотека Primo.AI.Server для использования моделей в RPA-проектах.

Для использования модели сначала потребуется запустить процесс инференса на целевой машине с компонентом Умный OCR. Этот шаг выполняется на стороне AI Server средствами интерфейса.

Далее следует шаг отправки запросов к серверу, который можно выполнить различными способами.

#### Способ 1 — API для внешних систем 
API для отправки OCR-запросов задокументирован в Swagger, который доступен по ссылке.....

#### Способ 2 — Роботы Primo RPA. 
Отправлять запросы могут и роботы Primo RPA. Для этого потребуется разработать RPA-проект с использованием библиотеки Primo.AI.Server. Проект разрабатывается в Primo RPA Studio. 

Библиотека содержит элементы для отправки асинхронных запросов к AI Server. Подробную информацию об элементах вы можете узнать здесь.


## Дополнительная информация

Компонент Умный OCR устанавливается на целевой машине и включает в себя:
* Primo.AI.IDP — data science-ядро с нейронными сетями и OCR. Используется для интеллектуальной обработки документов.
* Primo.AI.Agent — self-hosted веб-приложение, выполнено как NET8-приложение. Агент используется для управления IDP на целевой машине.


### Порядок работы в AI Server

1. Настройка целевой машины и машины сервера, которая включает в себя установку компонентов и их конфигурацию.
1. Выполнение административных настроек в Server AI:
   * Получение лицензий на машину сервера и агента каждой целевой машины.
   * Создание пользователей и назначение прав доступа с помощью ролей.
   * Создание сущностей целевых машин, типов моделей, проверка состояния запущенных служб.
1. Работа с проектом в Server AI, в рамках которого:
   * Выбирается тип модели для обучения или готовая модель от команды Primo RPA.
   * Тестируется отправка запросов при необходимости;
   * Запускается процесс инференса на доступной целевой машине, чтобы модель была готова принимать запросы.
1. Отправка запросов к Server AI с помощью API или роботов.
