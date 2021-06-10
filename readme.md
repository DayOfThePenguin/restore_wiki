## Connect to mysql with config that's in docker-compose
mysql -h 127.0.0.1 -u root -p 

## Restoring mariadb from sql files
https://mariadb.com/kb/en/restoring-data-from-dump-files/

## Get into container
docker exec -it 480fb3f04589 bash

## From in the container
mysql -u root -p\x

## Tune variables
set global read_buffer_size=2000000000;
set global max_allowed_packet=1000000000;
set global innodb_buffer_pool_size=16000000000;
set global key_buffer_size=8000000000;

Recommendations from [server vars that can increase insert speed](https://mariadb.com/kb/en/how-to-quickly-insert-data-into-mariadb/#server-variables-that-can-be-used-to-tune-insert-speed)

### To import
mysql db_name -h 127.0.0.1 -u root -p < file.sql

Categories took ~6 min
Redirects took ~6.5 hours

### Getting table sizes
https://chartio.com/resources/tutorials/how-to-get-the-size-of-a-table-in-mysql/

SELECT   TABLE_NAME AS `Table`,   ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size
(MB)` FROM   information_schema.TABLES WHERE   TABLE_SCHEMA = "wikipedia" ORDER BY   (DATA_LENGTH +
INDEX_LENGTH) DESC;

### Commands
USE wikipedia; # set DB
SHOW TABLES;
DESCRIBE table_name;
SELECT count(*) FROM table_name;

## Article Quality Reference
https://en.wikipedia.org/wiki/Wikipedia:Statistics

https://en.wikipedia.org/wiki/Wikipedia:Vital_articles
