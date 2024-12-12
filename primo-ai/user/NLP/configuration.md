# Настройка NLP-проекта 


## Предварительные условия

Создайте проект с типом **NLP-задачи**.

## Конфигурация

После создания проекта автоматически откроется страница настройки. Также на нее можно перейти позже, если выбрать на главной странице карточку нужного NLP-проекта.

Цель выполнения настроек — получить большую языковую модель, готовую обрабатывать NLP-запросы. Задачи, которые сможет решать модель, определяются ее навыками, указанными в ходе настройки. 

![](</primo-ai/resources/user/nlpproject/nlp_config.png>) 

На рисунке отмечены следующие элементы рабочей области:
* `1` — Область настройки LLM-модели. Это первый и обязательный шаг — каждую модель следует сконфигурировать до запуска на целевой машине или машинах. 
* `2` — Область выбора целевых машин для запуска LLM-модели. Чтобы запустить модель, сначала потребуется выбрать подходящую целевую машину, после чего произвести запуск модели на этой машине. 
* `3` — Область выбора навыков модели и их настройки. Это необязательный шаг — по умолчанию, если ни один навык не выбран, то модель сможет только генерировать тексты.
* `4` — Кнопка добавления новой конфигурации. В одном проекте может быть несколько конфигураций. NLP-проекты могут поддерживать несколько конфигураций,
* `5` — Иконка меню для управление конфигурацией. Каждую конфигурацию можно переименовать или удалить — соответствующие команды доступны при выборе иконки.
* `6` — Вкладка **Тестирование**. Позволяет отправлять тестовые запросы, просматривать ответы модели и корректировать ее поведение при необходимости.


## Параметры конфигурации

#### Основные параметры

1. **Выбор базовой модели** — тип базовой модели из выпадающего списка. Базовая модель — это предобученная на большом корпусе текстовых данных модель нейронной сети, которая может понимать и генерировать текст. Базовые модели входят в поставку AI Server, а также могут быть созданы дополнительно администратором сервиса.
  
   Значения, которые доступны по умолчанию:
   * `llama3.1-8B (Vllm)` — базовая модель на сервере Vllm. Этот тип базовой модели обрабатывает запросы быстрее и точнее, но более требователен к аппаратным характеристикам целевой машины.
   * `llama3.1-8B-GGUF (Llama)` — базовая модель на сервере Llama. Позволяет запускать большую языковую модель на низкотребовательной целевой машине. 

1. **Ключ маршрутизации по умолчанию** — этот ключ используется для маршрутизации запросов к модели без выбранных навыков. Такая модель будет способна только создавать текст.

#### Расширенные параметры

1. **LLM-движок** — тип движка, который ассоциирован с базовой моделью. Доступные значения:
    * `Vllm` — сервер для базовой модели на Vllm.
    * `Llama` — сервер для базовой модели на Llama.
1. **Размер контекстного окна** — объем текста, который модель рассматривает перед генерацией текста. По умолчанию `4096`.
1. **Адаптер** — пропустите этот параметр, он не поддерживается для NLP-задач.
1. **Выбор устройства** — тип устройства, который используется на целевой машине с сервером LLM. Доступные значения:
    * `CPU` — значение по умолчанию. Центральный процессор, выполняющий основные операции и управляющий работой компьютера.
    * `CUDA` — архитектура CUDA позволяет использовать графический процессор (GPU) от NVIDIA для повышения производительности параллельных вычислений. CUDA представляет собой набор инструментов и библиотек для работы с графическим процессором.

   Если вы выбрали `CPU`, установите:
   * **Кол-во используемых CPU** — количество ядер CPU, которые будет использовать контейнер с выбранным движком для генерации ответов. 

   Если вы выбрали `CUDA`, установите:
   * **Кол-во используемых GPU** — количество видеокарт. Если модель не помещается в VRAM одной GPU, используйте несколько видеокарт. 
   * **Загруженность видеокарты** — процент использования памяти видеокарты. 
   * **Кол-во памяти от хоста** — если модель не помещается в VRAM одной GPU, оставьте часть слоев LLM на хосте.

  
## Целевые машины

Целевая машина — логическая сущность в Server AI, которая представляет собой физическую или виртуальную машину (или группу машин) с агентом. Агент управляет моделью: запускает, останавливает, настраивает, отправляет запросы. 

В проект можно добавить только включенную и доступную целевую машину. Чтобы горизонтально масштабировать процесс, вы можете запустить модель сразу на нескольких машинах. При этом агент каждой целевой машины должен быть лицензирован. 

{% hint style="warning" %}
Если в списке целевых машин нет нужного значения, убедитесь, что машина была создана администратором на странице **Настройки > Целевые машины**, а также включена и доступна.
{% endhint %}

**Как запустить модель:**

1. Нажмите **Добавить машину**.
1. Выберите из выпадающего списка название машины. Добавленная машина будет ожидать запуска модели.
1. Чтобы запустить модель, переведите переключатель вправо.

   ![](</primo-ai/resources/user/nlpproject/run_llm_model.png>)  
  
   Начнется автоматический процесс запуска — он займет некоторое время.

1. Дождитесь, когда напротив всех стадий запуска будут проставлены галочки — это означает, что модель успешно запустилась и готова к работе.

   ![](</primo-ai/resources/user/nlpproject/nlp_statuses_model.png>) 

   Если вы обновите страницу, то вместо стадий запуска увидите только один статус — `Готова принимать запросы`.

   ![](</primo-ai/resources/user/nlpproject/model_is_ready.png>) 

Готово — теперь вы можете перейти к добавлению навыков модели.


**Ошибка при запуске модели**:

Если процесс запуска завершился ошибкой, то вместо статуса `Готова принимать запросы`, вы увидите индикатор ошибки. 

Ошибка может возникнуть в следующих случаях:
* На выбранной машине уже запущен процесс - ?.
* ??


**Как остановить модель**:

Вам может понадобиться остановить LLM-модель, чтобы выключить машину или запустить на ней модель в другом проекте. Для этого просто переведите переключатель влево. Дождитесь, чтобы переключатель стал доступен для редактирования — это означает, что модель остановилась. 

**Как удалить целевую машину**:

Чтобы удалить целевую машину из проекта, нажмите на меню рядом с именем машины и выберите **Удалить**.


## Навыки

Навык — это способность языковой модели выполнять определенные задачи, связанные с обработкой и созданием текста. Модель без навыков способна только создавать новый текст (соответствует навыку *Генерация*). 

Одной модели можно назначить несколько навыков. При указании навыка потребуется выбрать ключ маршрутизации — уникальный ключ, с помощью которого сервер выбирает модель и навык для обработки поступившего запроса. Вы можете дублировать навыки в одной конфигурации, но ключи маршрутизации повторяться не могут.

После выбора ключа, в конфигурацию автоматически загрузится файл контекста — это встроенный json-файл, который определяет поведение модели с навыком относительно будущих запросов. Файл контекста берется из профиля ключа маршрутизации — например, для всех встроенных ключей этот файл предзадан. Также файл может отсутствовать, если ключ был создан администратором, который не стал загружать файл. 

Файл контекста помогает улучшать качество ответов модели и генерировать более релевантные и точные ответы. Вы можете заменять файл контекста из профиля ключа собственным файлом — и таким образом влиять на поведение модели.

Структура файла контекста (.json):
* Секция `"input"` — пример входного текста, который могут отправить в запросе для определенного навыка.
* Секция `"keys"` — ключевые слова, которые помогут модели сосредоточиться на наиболее релевантной информации в тексте запроса.
* Секция `"output"` — пример ответа, который подскажет модели корректный вариант обработки текста, а также стиль изложения (более или менее формальный).

-----


После выбора ключа, в конфигурацию автоматически загрузится файл контекста — это json-файл с набором данных, который определяет поведение модели с указанным навыком относительно будущих запросов. Файл контекста помогает улучшать качество ответов модели и генерировать более релевантные и точные ответы. Эта цель достигается с помощью набора данных, прописанных в файле. ... это дополнительный контекст

Это инструмент тонкой настройки модели.

Структура файла контекста (.json):
* Секция `"input"` — пример входного текста, который могут отправить в запросе для определенного навыка.
* Секция `"keys"` — ключевые слова, которые помогут модели сосредоточиться на наиболее релевантной информации в тексте запроса.
* Секция `"output"` — пример ответа, который подскажет модели корректный вариант обработки текста, а также стиль изложения (более или менее формальный).


Сервер берет файл контекста из профиля ключа маршрутизации — например, для всех встроенных ключей этот файл предзадан. Для ключа, который создавал администратор, файл может отсутствовать — это означает, что при создании ключа администратор не стал загружать файл по умолчанию. Вы можете заменять файл контекста из профиля ключа собственным файлом — и таким образом влиять на поведение модели.



### Как добавить навык

1. Выберите **Добавить навык**.
1. Выберите навык из списка:
   * `Классификация` — ответ на запрос из заранее определенного списка вариантов ответов. 
   * `Суммаризация` — краткое изложение текста с акцентом на определенные темы.
   * `Экстракция` — извлечение из текста информации по заданным ключам поиска.
   * `Генерация` — генерация текста по заданным параметрам.
1. Выберите ключ маршрутизации запросов для данного навыка. 
1. После выбора ключа автоматически отобразится **файл с контекстом (.json)**. Вы можете:
   * скачать файл для просмотра;
   * заменить файл по умолчанию своим файлом;
   * отредактировать свой файл с контекстом, который вы загрузили вместо файла по умолчанию;
   * восстановить файл по умолчанию.

   ![](</primo-ai/resources/user/nlpproject/model_skill.png>)  


Новые навыки добавляются аналогично действиям выше.

{% hint style="warning" %}
Если в списке ключей маршрутизации нет нужного вам значения, убедитесь, что все необходимые ключи были созданы администратором на вкладке **Настройки > Ключи маршрутизации**.
{% endhint %}



