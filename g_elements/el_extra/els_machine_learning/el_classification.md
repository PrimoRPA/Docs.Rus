---
description: Classification
---

# Классификация

Элемент осуществляет классификацию входных данных на основе обученной модели. Модель, которую вы будете использовать, предварительно обучают с помощью элемента [Обучение модели классификации](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_machine_learning/el_classification_study).

![](<../../../.gitbook/assets/image (216).png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

#### Входные данные

* **Путь к модели\*** *[String]* — путь к файлу модели. Пример: `System.IO.Path.Combine(_Workflow.ProjectPath, "Models\\model.ml")`.
* **Данные\*** *[[System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-8.0&viewFallbackFrom=net-4.6.1)]* — входные данные для классификации.

#### Вывод

* **Результат** *[List<[Aura.MachineLearning.Model.MLNet.PredictionResultStr](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_machine_learning/datatypes/predictionresultstr)>]* — результат классификации.

## Пример использования

На странице [Learning](https://github.com/PrimoRPA/Learning) доступен RPA-проект, демонстрирующий работу элемента.

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив, запустите Primo Studio и откройте проект **MachineLearning**.
3. Выберите процесс `Classification.ltw` для просмотра.
