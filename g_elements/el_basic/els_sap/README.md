# SAP Front End

Для работы компонентов SAP Front End (за исключением BAPI), необходимо включить поддержку SAP UI Scripting.

Активация SAP UI Scripting

В SAP UI перейти в транзакцию RZ11

![](<../../../.gitbook/assets/image (821).png>)

В поле Param. Name ввести sapgui/user\_scripting

![](<../../../.gitbook/assets/image (970).png>)

Нажать Change Value

![](<../../../.gitbook/assets/image (833).png>)

В поле New Value ввести TRUE и нажать кнопку с дискетой

![](<../../../.gitbook/assets/image (961).png>)

**Перезагрузить SAP UI**

Далее в SAP UI нажать кнопку Customize Local Layout и выбрать Options

![](<../../../.gitbook/assets/image (851).png>)

Перейти в раздел Accessibility & Scripting и выбрать Scripting

![](<../../../.gitbook/assets/image (889).png>)

Поставить галку в пункте Enable scripting и убрать галки в пунктах Notify...

![](<../../../.gitbook/assets/image (783).png>)
