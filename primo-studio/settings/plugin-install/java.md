# Java плагин

При работе c Java в Студии версии 1.25.1 и выше рекомендуется учитывать перечисленные пункты:

1. ***Минимальная версия Java***: Java SE Runtime Environment (JRE) версии 7 Update 6 (7u6) и выше, так как Java Access Bridge включен по умолчанию, начиная с этой версии, но не активирован.

2. ***Java Access Bridge*:** Чтобы обеспечить доступность Java-элементов через Primo, необходимо включить Java Access Bridge. Как активировать:

   - Перейдите в Панель управления > Специальные возможности > Использование компьютера без дисплея.
   - Установите флажок «Enable Java Access Bridge».

3. ***Совместимость разрядности*:** Убедитесь, что разрядность установленной Java (например, 32-битная или 64-битная) соответствует разрядности Primo RPA Studio и Primo RPA Robot

4. ***Для старых версий Java*** (например, 1.6.0_31 и ниже), Java Access Bridge не интегрирован по умолчанию. В этом случае потребуется скачать и установить более актуальную версию Java SE (от 7u6 и выше) для совместимости.

5. ***Ссылки на архив версий*:** Архив старых версий Java доступен на официальном сайте Oracle https://www.oracle.com/java/technologies/downloads/archive/
https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/settings/plugin-install/java


  > Начиная с версии *Primo Studio 1.25.1, работа с Java-элементами гарантирована только при использовании Java версии **7u6* и выше.


### Как включить Java Access Bridge

1. Убедитесь, что установлена версия Java 7u6 или выше.  
2. Для активации Java Access Bridge выполните:  
   - *Панель управления > Специальные возможности > Использование компьютера без дисплея*.  
   - Установите флажок *Enable Java Access Bridge*.


### Для обновления Java:

1. Загрузите версию Java 7u6 или выше с [архива версий Oracle](https://www.oracle.com/java/technologies/downloads/archive/).  
2. Удалите старую версию Java и установите новую.  
3. Активируйте Java Access Bridge, как описано выше.


![](<../../../.gitbook/assets/image (772).png>)


