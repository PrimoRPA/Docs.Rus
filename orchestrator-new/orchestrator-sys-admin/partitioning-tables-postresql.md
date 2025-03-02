# Секционирование существующих таблиц с журналом Робота и Оркестратора для PostgreSQL

С общей информацией о секционировании вы можете ознакомиться на [официальном сайтк PostreSQL](https://postgrespro.ru/docs/postgresql/10/ddl-partitioning).

Для секционирования по месяцам нужно существующую таблицу подключить как раздел исторических данных.

Сначала для журнала робота. Создаём новую головную секционированную таблицу идентичной таблице Logs структуры под каким-нибудь новым именем, например, Logs2:
```
CREATE TABLE public."Logs2"
(
    "Id" uuid NOT NULL,
    "OrchTimestampUtc" timestamp without time zone NOT NULL,
    "Event" integer,
    "EntityId" text COLLATE pg_catalog."default",
    "UserId" text COLLATE pg_catalog."default",
    "TimestampUtc" timestamp without time zone,
    "OperationKey" uuid,
    "Signature" text COLLATE pg_catalog."default",
    "WorkerAdminName" text COLLATE pg_catalog."default",
    "Text" text COLLATE pg_catalog."default",
    "EventType" integer,
    "IP" text COLLATE pg_catalog."default",
    "TenantId" text COLLATE pg_catalog."default",
    "AssignmentId" integer,
    "RobotId" integer,
    "RobotKey" text COLLATE pg_catalog."default",
    "ProjectId" integer,
    "WorkerId" integer,
    "Type" integer,
    "ParsedDateEvent" timestamp without time zone,
    "ParsedType" integer,
    "ParsedElementName" text COLLATE pg_catalog."default",
    "ParsedElementId" text COLLATE pg_catalog."default",
    "ParsedElementClass" text COLLATE pg_catalog."default",
    "ParsedMessage" text COLLATE pg_catalog."default",
    "ScreenFilePath" text COLLATE pg_catalog."default",
    "OrchScreenFilePath" text COLLATE pg_catalog."default",
    "OrchScreenFilePathThumb" text COLLATE pg_catalog."default",
    "Node" text COLLATE pg_catalog."default",
    "ExtDataJson" text COLLATE pg_catalog."default",
    "RobotName" text COLLATE pg_catalog."default",
    "ProjectName" text COLLATE pg_catalog."default",
    "WorkerName" text COLLATE pg_catalog."default",
    "RdpUserName" text COLLATE pg_catalog."default",
    "LogType" integer NOT NULL,
    "ParsedElementNum" text COLLATE pg_catalog."default"
) partition by range ("OrchTimestampUtc");
```
Создаем секцию (можно создать сразу несколько, с запасом) с данными на будущее (даты приведены для примера, нужно будет заменить на актуальные):
```
create table "Logs_20230325" partition of "Logs2" 
   for values from ('2023-03-25') to ('2023-04-01');
```
Подготавливаем существующую таблицу с данными Logs – добавляем в неё ограничение на поле OrchTimestampUtc и проверяем это ограничение на данных таблицы:
```
begin;
   set local statement_timeout to '1s';
   alter table "Logs" add constraint "Logs_partbound_check" 
      check ("OrchTimestampUtc" < '2023-03-25' and "OrchTimestampUtc" is not null) not valid;
commit;

alter table "Logs" validate constraint "Logs_partbound_check";
```
Если `validate constraint` выдаёт ошибки, то надо проверить данные/ограничение, и по возможности, провести корректировки (например, удалить некорректные данные).

Всю миграцию надо завершить до наступления даты 2023-04-01, либо удалить ограничение:
```
alter table "Logs"  drop constraint "Logs_partbound_check";
```
и начать сначала.

Переименовываем таблицы и добавляем существующую таблицу (теперь она называется Logs_archive) как секцию к головной секционированной таблице Logs:
```
begin;
   set statement_timeout to '1s';
   alter table "Logs" rename to "Logs_archive";
   alter table "Logs2" rename to "Logs";
   alter table "Logs" attach partition "Logs_archive" for values from (MINVALUE) to ('2023-03-25');
commit;
```
Пока не настанет 2023-03-25, данные будут писаться в секцию Logs_archive (в старую архивную таблицу). Начиная с 2023-03-25 – в секцию Logs_20230325. 
Все запросы с фильтром по дате будут прозрачным для приложения образом идти через таблицу Logs.

Повторяем индексы на вновь созданной секции таблицы Logs_20230325 (если несколько секций, то для каждой секции):
```
CREATE INDEX "IX_Logs_20230325_EntityId"
    ON public."Logs_20230325" USING btree
    ("EntityId" COLLATE pg_catalog."default" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_20230325_Event"
    ON public."Logs_20230325" USING btree
    ("Event" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_20230325_OperationKey"
    ON public."Logs_20230325" USING btree
    ("OperationKey" ASC NULLS LAST)
    TABLESPACE pg_default;


CREATE INDEX "IX_Logs_20230325_ProjectId"
    ON public."Logs_20230325" USING btree
    ("ProjectId" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_20230325_RobotId"
    ON public."Logs_20230325" USING btree
    ("RobotId" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_20230325_RobotId_OperationKey_TimestampUtc"
    ON public."Logs_20230325" USING btree
    ("RobotId" ASC NULLS LAST, "OperationKey" ASC NULLS LAST, "TimestampUtc" DESC NULLS LAST)
    INCLUDE("Type", "LogType")
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_20230325_RobotKey"
    ON public."Logs_20230325" USING btree
    ("RobotKey" COLLATE pg_catalog."default" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_20230325_UserId"
    ON public."Logs_20230325" USING btree
    ("UserId" COLLATE pg_catalog."default" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_20230325_WorkerId"
    ON public."Logs_20230325" USING btree
    ("WorkerId" ASC NULLS LAST)
    TABLESPACE pg_default;
```

Повторяем аналогичные действия для журнала Оркестратора:
```
CREATE TABLE public."OrchEvents2"
(
    "Id" uuid NOT NULL,
    "OrchTimestampUtc" timestamp without time zone NOT NULL,
    "Event" integer NOT NULL,
    "EntityId" text COLLATE pg_catalog."default",
    "UserId" text COLLATE pg_catalog."default",
    "OperationKey" uuid,
    "Signature" text COLLATE pg_catalog."default",
    "WorkerAdminName" text COLLATE pg_catalog."default",
    "Text" text COLLATE pg_catalog."default",
    "EventType" integer,
    "IP" text COLLATE pg_catalog."default",
    "TenantId" text COLLATE pg_catalog."default",
    "AssignmentId" integer,
    "LogType" integer NOT NULL DEFAULT 1,
    "ProjectId" integer, 
  "ProjectName" text COLLATE pg_catalog."default",
   "NodeId" integer
) partition by range ("OrchTimestampUtc");


create table "OrchEvents_20230325" partition of "OrchEvents2" 
   for values from ('2023-03-25') to ('2023-04-01');

begin;
   set local statement_timeout to '1s';
   alter table "OrchEvents" add constraint "OrchEvents_partbound_check" 
      check ("OrchTimestampUtc" < '2023-03-25' and "OrchTimestampUtc" is not null) not valid;
commit;

alter table "OrchEvents" validate constraint "OrchEvents_partbound_check";

begin;
   set statement_timeout to '1s';
   alter table "OrchEvents" rename to "OrchEvents_archive";
   alter table "OrchEvents2" rename to "OrchEvents";
   alter table "OrchEvents" attach partition "OrchEvents_archive" for values from (MINVALUE) to ('2023-03-25');
commit;

CREATE INDEX "IX_OrchEvents_20230325_AllOrchTimestampUtc"
    ON public."OrchEvents_20230325" USING btree
    ("TenantId" COLLATE pg_catalog."default" ASC NULLS LAST, "Event" ASC NULLS LAST, "UserId" COLLATE pg_catalog."default" ASC NULLS LAST, "EventType" ASC NULLS LAST, "OrchTimestampUtc" DESC NULLS LAST)
    INCLUDE("EntityId", "OperationKey", "Signature", "WorkerAdminName", "Text", "IP", "AssignmentId", "LogType")
    TABLESPACE pg_default;

CREATE INDEX "IX_OrchEvents_20230325_EntityId_OrchTimestampUtc"
    ON public."OrchEvents_20230325" USING btree
    ("EntityId" COLLATE pg_catalog."default" ASC NULLS LAST, "OrchTimestampUtc" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_OrchEvents_20230325_Event_OrchTimestampUtc"
    ON public."OrchEvents_20230325" USING btree
    ("Event" ASC NULLS LAST, "OrchTimestampUtc" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_OrchEvents_20230325_UserId_OrchTimestampUtc"
    ON public."OrchEvents_20230325" USING btree
    ("UserId" COLLATE pg_catalog."default" ASC NULLS LAST, "OrchTimestampUtc" ASC NULLS LAST)
    TABLESPACE pg_default;
```
Секций с новыми данными сразу можно добавить с запасом несколько. Дальнейшее их создание и удаление старых секций можно автоматизировать на основе задачи по расписанию. 


## Автоматическое создание новых секций

Устанавливаем расширение `pg_cron` - его установка может отличаться для разных дистрибутивов Linux.

Копируем пакет с `pg_cron` в расшаренную папку, из которой будет производиться его установка. Переходим в эту папку:
```
# cd /srv/samba/shared/install/postgresql-13
```
Устанавливаем пакет:
```
# dnf -y install 'pg_cron_13-1.3.0-1.rhel8.x86_64.rpm'
```
Вносим изменения в файл postgresql.conf:  
Устанавливаем (или дописываем) 'pg_cron' в `shared_preload_libraries`:
```
# vim /var/lib/pgsql/13/data/postgresql.conf

shared_preload_libraries = 'pg_cron'
```

![](../../../orchestrator-new/resources/orchestrator-sys-admin/partitioning-postgres1.PNG)

Добавляем в конец файла строку:
```
cron.database_name= 'ltoolslogs'
```

![](../../../orchestrator-new/resources/orchestrator-sys-admin/partitioning-postgres2.PNG)

Даем возможность локально подключаться к БД без пароля будущему заданию – вносим изменение в `pg_hba.conf`:
```
# vim /var/lib/pgsql/13/data/pg_hba.conf

host     all      all     ::1/128    	trust
```

![](../../../orchestrator-new/resources/orchestrator-sys-admin/partitioning-postgres3.PNG)

Перезапускаем службу:
```
# systemctl restart postgresql-13
```
Создаем в БД ltoolslogs расширение `pg_cron`. Можно через какой-то менеджер для работы с PostgreSQL, например, `pgAdmin4`. Или из командной строки:
```
# sudo -i -u postgres psql -d ltoolslogs -c 'CREATE EXTENSION pg_cron'
```	
После этого проверим, что в БД ltoolslogs появились схема `cron` и необходимые для заданий объекты БД:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/partitioning-postgres4.PNG)

В БД ltoolslogs создаем процедуру для создания секций:
```
CREATE OR REPLACE PROCEDURE public.create_logs_part(
	)
LANGUAGE 'plpgsql'
AS $BODY$
DECLARE
   y integer;
   m integer;
   d1 timestamp;
   d2 timestamp;   
   part varchar(100);
BEGIN
   y := date_part('year', CURRENT_DATE);
   m := date_part('month', CURRENT_DATE) + 1;
   
   d1 = make_date(y, m, 1);
   IF m = 12 THEN
     d2 = make_date(y + 1, 1, 1);
   ELSE
     d2 = make_date(y, m + 1, 1);
   END IF;
   
   part := format('%s%s', y, CASE WHEN m > 9 THEN format('%s', m) ELSE format('0%s', m) END);
   
   if NOT EXISTS (
          SELECT FROM pg_catalog.pg_class c
          JOIN   pg_catalog.pg_namespace n ON n.oid = c.relnamespace
          WHERE  c.relname = format('Logs_%s', part)) then
	  
      EXECUTE format('create table "Logs_%s" partition of "Logs" for values from (''%s'') to (''%s'')', 
				   part,  to_char(d1, 'yyyy-mm-dd'), to_char(d2, 'yyyy-mm-dd'));
				   
	  EXECUTE format('CREATE INDEX "IX_Logs_%1$s_EntityId" 
    ON "Logs_%1$s" USING btree
    ("EntityId" COLLATE pg_catalog."default" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_Event"
    ON public."Logs_%1$s" USING btree
    ("Event" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_OperationKey"
    ON "Logs_%1$s" USING btree
    ("OperationKey" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_ProjectId"
    ON "Logs_%1$s" USING btree
    ("ProjectId" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_RobotId"
    ON "Logs_%1$s" USING btree
    ("RobotId" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_RobotId_OperationKey_TimestampUtc"
    ON "Logs_%1$s" USING btree
    ("RobotId" ASC NULLS LAST, "OperationKey" ASC NULLS LAST, "TimestampUtc" DESC NULLS LAST)
    INCLUDE("Type", "LogType")
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_RobotKey"
    ON "Logs_%1$s" USING btree
    ("RobotKey" COLLATE pg_catalog."default" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_UserId"
    ON "Logs_%1$s" USING btree
    ("UserId" COLLATE pg_catalog."default" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_Logs_%1$s_WorkerId"
    ON "Logs_%1$s" USING btree
    ("WorkerId" ASC NULLS LAST)
    TABLESPACE pg_default;', part);
   end if;
   
   if NOT EXISTS (
          SELECT FROM pg_catalog.pg_class c
          JOIN   pg_catalog.pg_namespace n ON n.oid = c.relnamespace
          WHERE  c.relname = format('OrchEvents_%s', part)) then
	  
      EXECUTE format('create table "OrchEvents_%s" partition of "OrchEvents" for values from (''%s'') to (''%s'')', 
				   part,  to_char(d1, 'yyyy-mm-dd'), to_char(d2, 'yyyy-mm-dd')); 
				   
	  EXECUTE format('CREATE INDEX "IX_OrchEvents_%1$s_AllOrchTimestampUtc"
    ON "OrchEvents_%1$s" USING btree
    ("TenantId" COLLATE pg_catalog."default" ASC NULLS LAST, "Event" ASC NULLS LAST, "UserId" COLLATE pg_catalog."default" ASC NULLS LAST, "EventType" ASC NULLS LAST, "OrchTimestampUtc" DESC NULLS LAST)
    INCLUDE("EntityId", "OperationKey", "Signature", "WorkerAdminName", "Text", "IP", "AssignmentId", "LogType")
    TABLESPACE pg_default;

CREATE INDEX "IX_OrchEvents_%1$s_EntityId_OrchTimestampUtc"
    ON "OrchEvents_%1$s" USING btree
    ("EntityId" COLLATE pg_catalog."default" ASC NULLS LAST, "OrchTimestampUtc" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_OrchEvents_%1$s_Event_OrchTimestampUtc"
    ON "OrchEvents_%1$s" USING btree
    ("Event" ASC NULLS LAST, "OrchTimestampUtc" ASC NULLS LAST)
    TABLESPACE pg_default;

CREATE INDEX "IX_OrchEvents_%1$s_UserId_OrchTimestampUtc"
    ON "OrchEvents_%1$s" USING btree
    ("UserId" COLLATE pg_catalog."default" ASC NULLS LAST, "OrchTimestampUtc" ASC NULLS LAST)
    TABLESPACE pg_default;', part); 
   end if;
   
END
$BODY$;
```
В БД ltoolslogs создаем задание, которое будет каждые 30 минут запускать созданную процедуру:
```
select cron.schedule('*/30 * * * *','CALL public.create_logs_part ();');
```
Для пересоздания задания нужно удалить запись о нем из таблицы `cron."job"` и создать задание заново.










