# Yandex Vision OCR

![](<../../../.gitbook/assets/image (406).png>)

Компонент, осуществляющий подключение к ядру OCR Yandex Vision.

Перед началом работы необходимо:

1\. Зарегистрироваться в Yandex Cloud.

2\. Зайти в консоль [https://console.cloud.yandex.ru/](https://console.cloud.yandex.ru/) и пополнить баланс.

3\. Перейти в папку и получить ее идентификатор.

![](<../../../.gitbook/assets/image (976).png>)

4\. На странице [https://cloud.yandex.ru/docs/cli/quickstart#install](https://cloud.yandex.ru/docs/cli/quickstart#install) перейти по ссылке.

![](<../../../.gitbook/assets/image (588).png>)

5\. Получить OAuth ID.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство      | Тип                | Описание                                                                                                                                                                     |
| ------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ID каталога\* | String             | ID каталога облака Yandex '[https://cloud.yandex.ru/docs/resource-manager/operations/folder/get-id](https://cloud.yandex.ru/docs/resource-manager/operations/folder/get-id)' |
| OAuth-Токен   | String             | OAuth-Токен в сервисе Яндекс.OAuth '[https://cloud.yandex.ru/docs/iam/operations/iam-token/create](https://cloud.yandex.ru/docs/iam/operations/iam-token/create)'            |
| API-Key       | String             | Ключ API '[https://cloud.yandex.ru/docs/iam/concepts/authorization/api-key](https://cloud.yandex.ru/docs/iam/concepts/authorization/api-key)'                                |
| Переменная    | LTools.OCR.OCRInst | Переменная для сохранения ссылки на ядро OCR                                                                                                                                 |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitYandex(wf, "ID каталога", "OAuth-токен", "API-key");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.OcrApp.InitYandex(wf, "ID каталога", "OAuth-токен", "API-key")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.OcrApp.InitYandex(wf, "ID каталога", "OAuth-токен", "API-key");
```
{% endtab %}
{% endtabs %}

