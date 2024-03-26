# Шаблоны проектов

Primo RPA Studio предоставляет возможность создавать проект из шаблона. Возможно использовать встроенный шаблон или создать его вручную.

## Встроенные шаблоны

Список доступных шаблонов находится в разделе меню **Файл ➝ Проект**. Для создания проекта достаточно кликнуть на нужный шаблон.

![](<../../.gitbook/assets1/project-templates-list.png>)

Шаблоны представлены на русском и английском языках:
* Robotic Enterprise Framework (REF) — robust and Resilient framework for building Orchestator-connected enterprise projects.
* Robotic Enterprise Framework (REF RU) — русскоязычный шаблон для создания надежных отказоустойчивых процессов, подключенных к Оркестратору.
* Linear Process (SEQ) — all-in-one template for building generic sequential processes.
* Linear Process (SEQ RU) — шаблон для создания полнофункциональных линейных процессов.

Демонстрационные проекты с ипользованием шаблонов можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning/tree/master):
1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив. Проекты по работе с шаблонами находятся в каталоге **StudioTemplatesProjectExample**:
   * *RPA Challenge Dispatcher* — демонстрирует линейный процесс. Данный процесс скачивает файл с сайта RPA Challenge и записывает каждую строку в очередь как транзакцию. В последствии процесс RPA Challenge Performer обработает элементы очереди.
   * *RPA Challenge Performer* — демонстрирует транзакционный процесс. Для данного процесса уже подготовлена очередь процессом RPA Challenge Dispatcher. Робот открывает сайт RPA Challenge и обрабатывает каждую транзакцию. В конце выдает время заполнения всех строк.
3. Откройте выбранный проект в Студии, дважды кликнув по файлу `project.ltp`.


## Пользовательский шаблон

Чтобы создать собственный шаблон, выполните следующие действия:

1. Создайте проект, который должен послужить шаблоном, и упакуйте его в архив `project.zip` (**Файл ➝ Экспорт ➝ Упаковать проект**). 
2. Выберите иконку для шаблона (в дальнейшем `icon.png`).
3. Создайте файл-манифест `manifest.xml`. Пример структуры файла:

```xml
<?xml version="1.0" encoding="utf-16"?>
<ProjectTemplateItem xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <Name>Наименование шаблона</Name>
    <Description>Описание шаблона</Description>
    <Version>Версия (1.0)</Version>
    <MainProcessPath>Имя основного процесса (Main.ltw)</MainProcessPath>
</ProjectTemplateItem>
```

4\.  Файлы `project.zip`, `icon.png` и` manifest.xml` поместите в соответствующую папку внутри каталога **ProjectTemplates** Студии.
