# Yandex Vision OCR

![](<../../../.gitbook/assets/image (406).png>)

Элемент производит подключение к ядру OCR Yandex Vision.

Перед началом работы:

1. Зарегистрируйтесь в Yandex Cloud.
2. Зайдите в консоль [https://console.cloud.yandex.ru/](https://console.cloud.yandex.ru/) и пополните баланс.
3. Перейдите в папку и получите ее идентификатор — данное значение потребуется указать в свойстве элемента **ID каталога**.

   ![Ссылка для перехода в каталог](<../../../.gitbook/assets/image (976).png>)

4. На странице [https://cloud.yandex.ru/docs/cli/quickstart#install](https://cloud.yandex.ru/docs/cli/quickstart#install) перейдите по ссылке из пункта 1.

   ![](<../../../.gitbook/assets1/windows_items/get-oauth-token.png>)
   
5. Скопируйте OAuth ID — данное значение потребуется указать в свойстве элемента **OAuth-Токен**.


## Свойства
Символ `*` в названии указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство      | Тип                | Описание                                                                                                                                                                     |
| ------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ID каталога\* | String             | [ID каталога](https://cloud.yandex.ru/docs/resource-manager/operations/folder/get-id) облака Yandex |
| OAuth-Токен   | String             | OAuth-токен в сервисе Яндекс.OAuth |
| API-Key       | String             | [Ключ API](https://cloud.yandex.ru/docs/iam/concepts/authorization/api-key). Если вы указали OAuth-Токен, то данное свойство заполнять не нужно |
| Переменная    | LTools.OCR.OCRInst | Переменная для сохранения ссылки на ядро OCR               |


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

