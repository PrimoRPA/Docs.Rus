# Управление шаблонами моделей

Шаблон модели (или *базовая модель*) — это заранее предобученная модель нейронной сети, готовая извлекать определенные свойства из изображений. Без шаблона модели невозможно:
* обучить собственную модель для обработки OCR-запросов;
* сконфигурировать большую языковую модель для обработки NLP-запросов.

Пользователь выбирает ту или иную базовую модель, когда выполняет настройки в проектах Умного OCR или NLP.

Администратор управляет базовыми моделями на странице **Настройки > Шаблоны моделей**. Здесь он имеет право добавлять шаблоны моделей, скачивать файлы загруженных шаблонов, удалять неиспользуемые шаблоны, изменять названия и описание шаблонов моделей. 


![](<../../../primo-ai/resources/admin/model-templates-actions.png>)

## Шаблон по умолчанию
Система поставляется с предустановленными шаблонами модели для компонентов Умный OCR и AI Текст. При использовании шаблона из поставки не потребуется совершать никаких дополнительных настроек на странице **Настройки ➝ Шаблоны моделей**. 

В поставку AI Server входят:
* `base-SmartOCR-01` — базовая модель для компонента Умный OCR, которая подходит как для обучения моделей-классификаторов, так и для моделей, занимающихся распознаванием данных в документах.
* `base-LLM-01 (Vllm)` — базовая LLM-модель, которая работает на движке Vllm. Способна быстро и точно обрабатывать запросы, но требовательна к аппаратным характеристикам целевой машины. Эту базовую модель следует использовать на машине с графической картой или высокопроизводительном CPU.
* `base-LLM-02 (Llama)` — базовая LLM-модель, которая работает на движке Llama. Её можно запускать на низкотребовательной целевой машине с CPU. Не поддерживает работу с GPU.
* `base-LLM-03 (Vllm)` — базовая LLM-модель, которая работает на движке Vllm. Данную модель следует использовать на машине с графической картой или высокопроизводительном CPU.

Используйте в проектах шаблон из поставки, если у вас нет потребности добавлять свой шаблон.

## Управление 

### Добавить шаблон модели

1. Перейдите в раздел **Настройки ➝ Шаблоны моделей**. 
1. Нажмите кнопку **Добавить шаблон модели**. Откроется форма вида:

   ![](<../../../primo-ai/resources/admin/model-templates-add.png>)
   
1. В поле **Название** укажите название будущего шаблона модели. 
1. В поле **Описание** добавьте краткую информацию о назначении шаблона.
1. В поле **Тип проекта** выберите значение из списка:
   * `Умный OCR` — проект, который предназначен для обработки сканов документов с помощью сверточных нейросетей.
   * `AI Текст` — проект для решения задач с помощью больших языковых моделей.
1. Если вы выбрали тип проекта `AI Текст`, то дополнительно укажите:
   * **Тип** — разновидность компонента. Доступные значения:
     * `NLP` — модель решает задачи, в которых требуется обрабатывать текст на естественном языке (например, на русском, английском).
     * `Экспертная система` — в настоящий момент не используется. Значение добавлено для будущих версий.
   * **Движок** — тип движка, на котором должна работать базовая модель. Доступные значения:
     * `Vllm` — для вычислений на графической карте или высокопроизводительном CPU.
     * `Llama` — для вычислений на CPU. В настоящий момент не поддерживается для GPU.
1. Перетащите в область для загрузки свой ZIP-архив с файлом шаблона модели. Файл(-ы) требуется упаковать в архив самостоятельно.
1. Нажмите **Сохранить**.

### Скачать шаблон модели

1. Перейдите в раздел **Настройки ➝ Шаблоны моделей**.
1. В таблице шаблонов моделей найдите нужную запись и нажмите значок ☰ для вызова меню действий.
1. Выберите пункт **Скачать**.
1. Дождитесь окончания скачивания ZIP-архива с файлом шаблона.

### Редактировать шаблон модели

1. Перейдите в раздел **Настройки ➝ Шаблоны моделей**.
2. В таблице шаблонов моделей найдите нужную запись и нажмите значок ☰ для вызова меню действий.
3. Выберите пункт **Редактировать**.
4. Для изменения будут доступны только параметры:
   * *название;*
   * *описание.*
6. Нажмите **Сохранить**.

### Удалить шаблон модели

{% hint style="warning" %}
**Важно**. Не удаляйте Базовую модель, чтобы не нарушать работу системы.
{% endhint %}


1. Перейдите в раздел **Настройки ➝ Шаблоны моделей**.
2. В таблице шаблонов моделей найдите нужную запись и нажмите значок ☰ для вызова меню действий.
3. Выберите пункт **Удалить**.
4. Подтвердите действие.

