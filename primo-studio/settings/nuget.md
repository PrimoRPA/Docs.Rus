# NuGet

Primo Studio позволяет подключать собственные источники пакетов NuGet. Для этого можно использовать:
* раздел меню **Файл > Настройки > Network > Nuget**;
* либо глобальную конфигурацию Nuget: см. статью Microsoft [«Команда sources (Интерфейс командной строки NuGet)](https://docs.microsoft.com/ru-ru/nuget/reference/cli-reference/cli-ref-sources)».

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

В разделе **Network > Nuget** для управления источниками имеются кнопки: «Создать», «Редактировать», «Удалить». Они отображаются в правом верхнем углу в виде иконок (см. скриншот выше). 

При создании источника появится окно:

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Обязательными к заполнению являются поля **Наименование** и **Источник**. 

После указания и сохранения настроек новый источник добавится в окне [Управления зависимостями](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/manage-dependencies#menedzher-zavisimostei). Пример:

![](../../.gitbook/assets/new-source-nuget-1.png)

## Дополнительно 
В качестве источника также можно указать и [локальный сервер NuGet](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/nuget), который входит в комплект поставки Оркестратора.
