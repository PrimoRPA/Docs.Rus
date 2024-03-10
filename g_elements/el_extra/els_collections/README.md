# Primo.Collections

Библиотека **Primo.Collections** позволяет автоматизировать работу с таблицами. 

В библиотеку входят следующие элементы:
* [**Построить таблицу**](https://docs.primo-rpa.ru/g_elements/el_extra/els_collections/els_data_tables/build) — создает таблицу на основе данных, указанных в Мастере. Результат сохраняется в переменную типа DataTable.
* [**Соединить таблицы**](https://docs.primo-rpa.ru/g_elements/el_extra/els_collections/els_data_tables/join) — производит объединение двух таблиц по указанным столбцам.
* [**Изменить значение**](https://docs.primo-rpa.ru/g_elements/el_extra/els_collections/els_data_tables/updaterowitem) — обновляет значение строки в таблице DataTable в соответствии с указанным столбцом. 
* [**Получить значение**](https://docs.primo-rpa.ru/g_elements/el_extra/els_collections/els_data_tables/getrowitem) — извлекает значение строки из таблицы DataTable в соответствии с указанным столбцом.

Перечисленные элементы станут доступны только после установки библиотеки. Они будут находиться на панели элементов в группе **Данные > Таблицы**. 

![](<../../../.gitbook/assets1/library-collections-primo.png>)


## Установка библиотеки

[Скачайте](https://www.nuget.org/packages/Primo.Collections) пакет **Primo.Collections** с портала NuGet.

Откройте Primo RPA Studio и нажмите в главном меню кнопку **Управление зависимостями** <img src="../../../.gitbook/assets/managePackages32.png" alt="" data-size="line">.

![](<../../../.gitbook/assets1/управление зависимостями.png>)

В окне **Управление зависимостями** перейдите на вкладку **Студия**. Выберите опцию загрузки и укажите путь к скачанному файлу пакета.

Далее в поисковой строке управления зависимостями введите Primo.Collection. Установите найденный пакет и сохраните изменения.

Готово - библиотека **Primo.Collection** установлен в качестве зависимости Студии. Немного подождите, пока зависимость загрузится, и перейдите на панель элементов.
