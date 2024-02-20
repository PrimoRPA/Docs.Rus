# Поиск изображений

Элемент осуществляет поиск и классификацию знакомых изображений внутри изображения.

![](<../../../.gitbook/assets/image (29).png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

#### Входные данные

1. **Путь к файлу\*** *[String]* — путь к файлу изображения, в котором осуществляется поиск.
2. **Путь к TensorFlow\*** *[String]* — путь к папке с обученной моделью TensorFlow.

#### Вывод

* **Результат** *[List<Aura.MachineLearning.Model.[ImageObjectResult](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_machine_learning/datatypes/imageobjectresult)>]* — массив найденных объектов.



