# Назва реестру

## Імпорт опублікованного датасету

- [Скрипт імпорту та нормалізації](/путь/від/корня)

## Створення бази даних

```sql
CREATE TABLE opendata.minjustEdrUO (
    id                   uuid DEFAULT gen_random_uuid() NOT NULL ,
    name                 varchar(100)   ,
    shortName            varchar(100)   ,
    edrpou               integer  NOT NULL ,
    address              varchar(100)   ,
    pinxed               integer   ,
    bossName             varchar(100)   ,
    kvedFull             varchar(255)   ,
    status               varchar(100)   ,
    kved                 varchar(5)   ,
    CONSTRAINT Pk_defolt_id_0 PRIMARY KEY ( id )
 );
```