# Домашнее задание к занятию "`Работа с данными (DDL/DML)`" - `Тен Денис`

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

### Решение Задание 1

Создание пользователя sys_temp
```sql
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password';
```

Назначение прав
```sql
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';
```
Получение списка пользователей в базе данных
```sql
SELECT user FROM mysql.user;
```

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/39d42bae-bcf0-4d79-b6d3-5085895f6b47)

Получение списка прав для пользователя sys_temp

```sql
SHOW GRANTS FOR 'sys_temp'@'localhost';
```
![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/97f2c37f-8671-4449-a11e-975ffaeaeccf)

Подключение под пользователем sys_temp через консоль

```
mysql -u sys_temp -p
```
![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/4aac3500-d5b6-46c6-bd64-9c5ab8e4e2ff)

Подключение под пользователем sys_temp через DBeaver

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/27846cd7-18a4-4db0-97ab-0b8fa9612a7a)

Меняем тип аутентификации с sha2

```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

Создание базы sakila

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/9ab1b838-c813-44a0-a99f-9a9650e21e0b)


Восстановление схемы

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/2f96458c-b624-4d30-9d7d-fe44aac293db)


Восстановление данных

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/6181c221-ad4d-4546-92dc-2790b3c49be8)

ER - диаграмма

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/2aec7ed8-5118-404e-a8de-2d426cbdc400)

Просмотр таблиц через CLI

```sql
use sakila
SHOW TABLES;
```

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/ddc5dfef-cf16-4b38-91a6-26028b5d9afc)



### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```

### Решение Задание 2

```sql
SELECT TABLE_NAME, COLUMN_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_SCHEMA = 'sakila' AND COLUMN_KEY = 'PRI';
```
```table
+---------------+--------------+
| TABLE_NAME    | PRIMARY_KEY  |
+---------------+--------------+
| actor         | actor_id     |
| address       | address_id   |
| category      | category_id  |
| city          | city_id      |
| country       | country_id   |
| customer      | customer_id  |
| film          | film_id      |
| film_actor    | actor_id     |
| film_actor    | film_id      |
| film_category | category_id  |
| film_category | film_id      |
| film_text     | film_id      |
| inventory     | inventory_id |
| language      | language_id  |
| payment       | payment_id   |
| rental        | rental_id    |
| staff         | staff_id     |
| store         | store_id     |
+---------------+--------------+
```

![image](https://github.com/killakazzak/12-02-sdb-hw/assets/32342205/c0badbff-51c1-4644-9cad-ff8bb82498fd)


## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

### Решение Задание 3*







