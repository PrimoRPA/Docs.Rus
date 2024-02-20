# Классификация

Элемент осуществляет классификацию на основе обученной модели.

![](<../../../.gitbook/assets/image (216).png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**«Входные данные»**:

* **Путь к модели\*** *[String]* — путь к файлу модели. Пример: `значение`.
* **Данные\*** *[System.Data.DataTable]* — данные для классификации. Пример: `значение`.

**«Вывод»**:

* **Результат** *[List<Aura.MachineLearning.Model.MLNet.[PredictionResultStr](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_machine_learning/datatypes/predictionresultstr)>]* — результат классификации.
