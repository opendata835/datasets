# Перелік об'єктів комунальної власності

## Створення бази даних

Потребує наявність у базі ["Єдиний державний реєстр юридичних осіб, фізичних осіб - підприємців та громадських формувань"](/minjust/01)



```sql
CREATE SCHEMA opendata;

CREATE TABLE opendata.omsOD02object ( 
	id                   uuid DEFAULT gen_random_uuid() NOT NULL ,
	ownerId              uuid   ,
	ownerEdrpuo          integer   ,
	ownerName            varchar(255)   ,
	adressId             uuid   ,
	adressName           varchar(255)   ,
	name                 varchar(255)   ,
	area                 numeric(5,2)   ,
	landАrea             numeric(5,2)   ,
	CONSTRAINT Pk_defolt_id_2 PRIMARY KEY ( id )
 );

COMMENT ON COLUMN opendata.omsOD02object.ownerId IS 'id у реестрі ЕДР';

COMMENT ON COLUMN opendata.omsOD02object.ownerEdrpuo IS 'ЕДРПУО власника';

COMMENT ON COLUMN opendata.omsOD02object.ownerName IS 'Назва властника';

COMMENT ON COLUMN opendata.omsOD02object.adressId IS 'Адресний реестр';

COMMENT ON COLUMN opendata.omsOD02object.adressName IS 'Адреса';

COMMENT ON COLUMN opendata.omsOD02object.name IS 'Назва обьекту';

COMMENT ON COLUMN opendata.omsOD02object.area IS 'Площадь участка';

COMMENT ON COLUMN opendata.omsOD02object.landАrea IS 'Площадь участка обьекта';

CREATE TABLE opendata.omsOD02PartObject ( 
	id                   uuid DEFAULT gen_random_uuid() NOT NULL ,
	objectId             uuid   ,
	name                 varchar(255)   ,
	adressId             integer   ,
	adressName           varchar(100)   ,
	area                 numeric(5,2)   ,
	landАrea             numeric(0,2)   ,
	CONSTRAINT Pk_defolt_id_3 PRIMARY KEY ( id ),
	CONSTRAINT Fk_omsOD02PartObject_omsOD02object FOREIGN KEY ( id ) REFERENCES opendata.omsOD02object( id )  
 );

COMMENT ON TABLE opendata.omsOD02PartObject IS 'Составные части обьекта при наличии';

COMMENT ON COLUMN opendata.omsOD02PartObject.objectId IS 'ID записи в реестре обьектов';

COMMENT ON COLUMN opendata.omsOD02PartObject.adressId IS 'ID в адресном реестре';

COMMENT ON COLUMN opendata.omsOD02PartObject.adressName IS 'Адрес';

COMMENT ON COLUMN opendata.omsOD02PartObject.landАrea IS 'Площадь участка';

```