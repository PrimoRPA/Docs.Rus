# Chrome

{% hint style="warning" %}
Если вы меняете версию манифеста для расширения, то сначала удалите расширение на базе старого манифеста, и только затем устанавливайте новое.
{% endhint %}

После каждого обновления Студии:
* Переустанавливайте расширение браузера.
* Либо соблюдайте рекомендации при [обновлении](https://docs.primo-rpa.ru/primo-rpa/primo-studio/installation/update) Студии, касающиеся файла `manifest_ch.json`. Исключением является ситуация, когда расширение было установлено с помощью [скриптов](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/autoinstall-browser-extension).

## Способы установки

Перейдите в раздел Студии **Файл > Настройки > Инструменты > Расширения**. Дальнейшие шаги зависят от выбранного способа установки.

### Магазин (текущий пользователь)

Cпособ установки по умолчанию. Требуется подключение к интернету.

1. Под иконкой браузера Chrome выберите из списка значение **Магазин (текущий пользователь)**. 

   ![](../../../.gitbook/assets/chrome-ext-machine.png)

1. Над иконкой браузера определите состояние параметра **Использовать манифест V3**:
   * **галочка отсутствует** — значение по умолчанию. В этом случае будет установлено расширение на основе Manifest V2. Нумерация расширения имеет вид 1.xx. Если вы выбрали этот вид расширения, ознакомьтесь с рекомендациями по добавлению [политики](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/settings/plugin-install#osobennosti-raboty-rasshireniya-s-manifest-v2), которая разрешает пользоваться расширениями для V2.
   * **галочка установлена** — установится расширение на основе нового Manifest V3. Нумерация расширения имеет вид 3.xx. Поскольку расширение на базе V3 является новым, рекомендуется сначала проверить работоспособность RPA-проекта в Студии и только затем использовать в Оркестраторе или Robor Runner'е. 

1. Нажмите на иконку Chrome.

   ![](../../../.gitbook/assets/chrome-icon-white-store-user.png)
   
Расширение автоматически установится из [интернет-магазина Chrome](https://chrome.google.com/webstore/detail/primo-rpa-extension/pbdnfhljkbaiibahdfcmgnfpapchlmmp) и зарегистрируется в реестре Windows в ветке текущего пользователя.

### Упакованное расширение

Установка не требует подключения к интернету. 

1. Под иконкой браузера Chrome выберите из выпадающего списка значение **Упакованное**.

   ![](../../../.gitbook/assets/chrome-ext-packed.png)

1. Над иконкой браузера определите состояние параметра **Использовать манифест V3**: 
   * **галочка отсутствует** — значение по умолчанию. В этом случае будет установлено расширение на основе Manifest V2. Нумерация расширения имеет вид 1.xx. Если вы выбрали этот вид расширения, ознакомьтесь с рекомендациями по добавлению [политики](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/settings/plugin-install#osobennosti-raboty-rasshireniya-s-manifest-v2), которая разрешает пользоваться расширениями для V2.
   * **галочка установлена** — установится расширение на базе нового манифеста V3. Нумерация расширения имеет вид 3.xx. Поскольку расширение на базе V3 является новым, рекомендуется сначала проверить работоспособность RPA-проекта в Студии и только затем использовать в Оркестраторе или Robor Runner'е. 
1. Нажмите на иконку Chrome — откроется окно c сохраненными файлами расширения и экземпляр браузера Chrome.

   ![](../../../.gitbook/assets/chrome-files-list.png)
   
1. В браузере Chrome перейдите в раздел **Настройки > Расширения > Управление расширениями**.
1. Перетащите файл `chrome.crx` в окно Chrome.
1. Нажмите кнопку **Установить расширение**.

{% hint style="info" %}
Если у вас нет кнопки **Установить расширение**, включите режим разработчика.
{% endhint %}



### Распакованное расширение

Этот способ установки не требует подключения к интернету.

1. Под иконкой браузера Chrome выберите значение **Распакованное**.
1. Над иконкой браузера определите состояние параметра **Использовать манифест V3**: 
   * **галочка отсутствует** — значение по умолчанию. В этом случае будет установлено расширение на основе Manifest V2. Нумерация расширения имеет вид 1.xx. Если вы выбрали этот вид расширения, ознакомьтесь с рекомендациями по добавлению [политики](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/settings/plugin-install#osobennosti-raboty-rasshireniya-s-manifest-v2), которая разрешает пользоваться расширениями для V2.
   * **галочка установлена** — установится расширение на базе нового манифеста V3. Нумерация расширения имеет вид 3.xx. Поскольку расширение на базе V3 является новым, рекомендуется сначала проверить работоспособность RPA-проекта в Студии и только затем использовать в Оркестраторе или Robor Runner'е. 
1. Далее нажмите на иконку Chrome. По нажатию иконки откроются:
   * экземпляр браузера Chrome;
   * окно с сохраненными файлами расширения:
 
   ![](../../../.gitbook/assets/chrome-files-list.png)
   
   * окно инсталляции с подсказками и полем ввода — с ним пока ничего не делаем:
 
   ![](../../../.gitbook/assets/chrome-install-id.png)

1. В браузере Chrome перейдите в раздел **Настройки > Расширения > Управление расширениями**.
1. В управлении расширениями нажмите на кнопку **Загрузить распакованное расширение** (Load unpacked) — цифра 1 на рисунке.

   *Если такой кнопки нет, включите режим разработчика — цифра 2 на рисунке.*

   ![](../../../.gitbook/assets/chrome-extensions.png)

1. Проверьте, что в окне загрузки указан путь до сохраненных файлов расширения (1 на рисунке), и нажмите кнопку **Выбор папки** (2 на рисунке). Пример пути: `C:\Program Files\Primo\Primo Studio x64\Extensions\Chrome`:

 ![](../../../.gitbook/assets/extensions-path-chrome.png)

1. Находясь в разделе расширений браузера Chrome, скопируйте идентификатор установленного расширения. Если его не видно полностью, нажмите кнопку **Сведения**:

   ![](../../../.gitbook/assets/id-extensions-chrome.png)

1. Вставьте скопированный идентификатор в окно инсталляции (см. шаг 2) и нажмите **ОК**:

   ![](../../../.gitbook/assets/install-id-extensions-chrome.png)


### Магазин (машина)

Требуется подключение к интернету.

1. В настройках Студии, под иконкой браузера Chrome, выберите из списка значение **Магазин (машина)**.
2. Нажмите на иконку Chrome.
3. Расширение автоматически установится из [интернет-магазина Chrome](https://chrome.google.com/webstore/detail/primo-rpa-extension/pbdnfhljkbaiibahdfcmgnfpapchlmmp) и зарегистрируется в ветке реестра Windows. 



