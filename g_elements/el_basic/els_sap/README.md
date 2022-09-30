# SAP Front End

Для работы компонентов SAP Front End (за исключением BAPI), необходимо включить поддержку SAP UI Scripting.

**Активация SAP UI Scripting**

В SAP UI перейти в транзакцию RZ11

![](<../../../.gitbook/assets/image (81).png>)

В поле Param. Name ввести sapgui/user\_scripting

![](<../../../.gitbook/assets/image (192).png>)

Нажать Change Value

![](<../../../.gitbook/assets/image (123).png>)

В поле New Value ввести TRUE и нажать кнопку с дискетой

![](<../../../.gitbook/assets/image (186).png>)

**Перезагрузить SAP UI**

Далее в SAP UI нажать кнопку Customize Local Layout и выбрать Options

![](<../../../.gitbook/assets/image (56).png>)

Перейти в раздел Accessibility & Scripting и выбрать Scripting

![](<../../../.gitbook/assets/image (167).png>)

Поставить галку в пункте Enable scripting и убрать галки в пунктах Notify...

![](<../../../.gitbook/assets/image (34).png>)
