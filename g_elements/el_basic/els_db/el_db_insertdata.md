---
description: Insert
---

# Вставка данных

![](<../../../.gitbook/assets/бд. вставка данных.png>)

Элемент производит вставку данных в указанную таблицу базы данных (БД).

![](<../../../.gitbook/assets1/insert.png>)



## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство          | Тип                                                                                                      | Описание                                                                                                     | Пример     |
| ----------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ---------- |
| **База данных:**  | | *Группа свойств для установки подключения к базе данных. Заполняется в том случае, когда элемент «Вставка данных» используется вне контейнера [«Присоединиться к БД»](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_insertdata)* | |
| Соединение с БД\* | LTools.Database.DatabaseInst | Название переменной, хранящей инстанс соединения с БД. Используется для более быстрого подключения к уже активному соединению. Если переменная указана, то свойства «Тип БД» и «Строка соединения» заполнять не нужно | |
| Строка соединения | String | Строка соединения с БД. Строку можно сформировать автоматически по кнопке <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> — в этом случае откроется окно мастера (Wizard) | <p>Ole DB:</p> <p>`"Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI"`</p> <p>PostgreSQL:</p> <p> `"Host=<host>;Port=5432;Password=<password>;Username=<username>;Database=<dbname>"`</p> <p>ODBC:</p> <p>`"DRIVER=<ODBC Driver>; SERVER=<host>; PORT=<port number>;DATABASE=<dbname>; USER=<username>; PASSWORD=<password>"`</p> |
| Тип БД            | LTools.Database.Model.DatabaseTypes | Тип подсоединяемой базы данных. Доступные значения: <p>1. Ole DB — по умолчанию.</p> <p>2. Postgre Sql.</p> <p>3. ODBC</p> | `Postgre Sql` |
| **Вывод:**        | | | |     
| Кол-во            | Int32                                                                                                    | Итоговое количество вставленных строк  | |
| **Данные:**       | | | |
| Точное совпадение | Boolean                                                                                                   |В базу данных импортируются все колонки из исходной таблицы или только совпадающие. **Функция доступна с версии Студии 1.24.8*  | |
| **Данные запроса:** | | | |
| Данные\*          | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0) | Данные в виде таблицы. Укажите название переменной         | |
| Таблица\*         | String                                                                                                   | Название таблицы в БД, в которую вы хотите вставить данные | `"table1"` |
| Таймаут\*         | Int32                                                                                                    | Таймаут запроса в секундах  | `10000` |

### Улучшение производительности

С версии 1.24.8 в Студии процесс импорта данных из DataTable в базу данных был значительно улучшен. За счет объединения всех операций вставки (Insert) в одну транзакцию скорость загрузки больших таблиц увеличена примерно в 2 раза.

Добавлено новое свойство — **"Точное совпадение колонок" [Boolean]**:
  - *Включено:* Все колонки из DataTable будут импортированы в базу данных. Если в DataTable есть колонки, которых нет в базе данных, произойдет ошибка.
  - *Отключено:* Импортируются только те колонки, которые совпадают по именам с колонками в базе данных.


### Окно мастера 

:small_blue_diamond: *Для ODBC мастер отсутствует.*

Свойство **Строка соединения** имеет кнопку <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> — при ее нажатии появится мастер создания строки соединения. Окно мастера будет отличаться для разных БД — убедитесь, что свойство **Тип БД** заполнено верно. 

Мастер для Ole DB:

![Для Ole DB](<../../../.gitbook/assets/image (301).png>)

Мастер для PostgreSQL:

![Для Postgre Sql](<../../../.gitbook/assets/image (383).png>)

После заполнения полей мастера и нажатия кнопки **OK** строка соединения сформируется автоматически и будет записана в соответствующее свойство.

Рассмотрим пример заполнения мастера для PostgreSQL. В свойстве **Тип БД** указываем `Postgre Sql`. После чего вызываем мастер и заполняем параметры подключения: 

![Заполненные параметры подключения к Postgre Sql](<../../../.gitbook/assets1/WFConnectDatabase-master.png>)

Нажимаем **Тест**, чтобы убедиться, что подключение настроено успешно. После чего сохраняем настройки. В свойстве **Строка соединения** автоматически сформировалось значение из нашего мастера: `"Host=localhost;Port=5432;Password=pass;Username=postgres;Database=postgres"`.



## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Database.DatabaseApp app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
int res = app.Insert("table", data);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI")
res = app.Insert("table", da
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI"); 
var res = app.Insert("table", data);
```
{% endtab %}
{% endtabs %}
