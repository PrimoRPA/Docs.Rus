---
description: Prediction
---


# Предсказание

Элемент осуществляет предсказание на основе обученной модели. Модель предварительно обучают с помощью элемента [**Обучение модели предсказания**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_machine_learning/el_prediction_study).

![](<../../../.gitbook/assets/image (232).png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

#### Входные данные

1. **Путь к модели\*** *[String]* — путь к файлу модели. Пример: `System.IO.Path.Combine(_Workflow.ProjectPath, "Models\\model.ml")`.
2. **Данные\*** *[System.Data.DataTable]* — входные данные для предсказания.


#### Вывод

* **Результат** *[List<[Aura.MachineLearning.Model.MLNet.PredictionResultFloat](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_machine_learning/datatypes/predictionresultfloat)>]* — результат предсказания.
