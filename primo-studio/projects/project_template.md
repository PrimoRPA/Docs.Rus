# Шаблоны проектов

Primo RPA Studio предоставляет возможность создавать проект из шаблона. Возможно использовать встроенный шаблон или создать его вручную.

## Встроенный шаблон

Список доступных шаблонов находится в разделе меню **Файл ➝ Проект**. Для создания проекта достаточно кликнуть на нужный шаблон.

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

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
