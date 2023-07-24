# Домашнее задание Индексы-Неклюдов Михаил


#Задание 1.

SELECT TABLE_SCHEMA, SUM(INDEX_LENGTH) / SUM(DATA_LENGTH) * 100

FROM INFORMATION_SCHEMA.TABLES

WHERE TABLE_SCHEMA = 'sakila';

![VirtualBox_Debian11-master_24_07_2023_09_53_16](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/0e8de20f-00d0-4b44-8efe-a82ff6058749)




#Задание 2.

Среди узких мест нужно отметить, что DISTINCT удаляет дубликаты и если среди пользователей есть тезки, то будет показан только один пользователь. В изучаемой базе тезок нет, но использование этого оператора излишне.

Судя по изначальному запросу нужно получить фамилиии и имена покупателей, которые заплатили за аренду и размер платы на 30 июля 2005 года.

Для того, что сделать такую выборку достаточно объединить таблицы customer и payment по customer_id. Нет необходимости использовать оконную функцию и большое количество условий условнного оператора.

Запрос будет выглядеть как-то так.

SELECT concat(c.last_name, ' ', c.first_name) as фамилия_имя, SUM(p.amount) as сумма_платежа

from customer c

INNER JOIN payment p on p.customer_id = c.customer_id

where date(p.payment_date) = '2005-07-30'

GROUP BY фамилия_имя

![VirtualBox_Debian11-master_24_07_2023_11_07_56](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/ad3232a6-f8b6-4dcc-88ca-f4be707ecf93)

# Explain analyze Запроса

Limit: 200 row(s)  (actual time=4.79..4.82 rows=200 loops=1)

    -> Table scan on <temporary>  (actual time=4.78..4.81 rows=200 loops=1)
    
        -> Aggregate using temporary table  (actual time=4.78..4.78 rows=391 loops=1)
        
            -> Nested loop inner join  (cost=2220 rows=1757) (actual time=0.0502..4.42 rows=634 loops=1)
            
                -> Filter: ((p.payment_date >= TIMESTAMP'2005-07-30 00:00:00') and (p.payment_date < <cache>(('2005-07-30' + interval 1 day))))  (cost=1606 rows=1757) (actual time=0.034..4 rows=634 loops=1)
                
                    -> Table scan on p  (cost=1606 rows=15813) (actual time=0.0267..2.96 rows=16044 loops=1)
                    
                -> Single-row index lookup on c using PRIMARY (customer_id=p.customer_id)  (cost=0.25 rows=1) (actual time=516e-6..536e-6 rows=1 loops=634)


Использование индекса payment_date

show INDEX from payment

![VirtualBox_Debian11-master_24_07_2023_13_20_04](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/bcc59d59-549f-4024-8320-18f4878ce314)

# Explain analyze Запроса после индексации

Limit: 200 row(s)  (actual time=1.26..1.28 rows=200 loops=1)

    -> Table scan on <temporary>  (actual time=1.26..1.28 rows=200 loops=1)
    
        -> Aggregate using temporary table  (actual time=1.26..1.26 rows=391 loops=1)
        
            -> Nested loop inner join  (cost=507 rows=634) (actual time=0.0223..0.979 rows=634 loops=1)
            
                -> Index range scan on p using data_data over ('2005-07-30 00:00:00' <= payment_date < '2005-07-31 00:00:00'), with index condition: ((p.payment_date >= TIMESTAMP'2005-07-30 00:00:00') and (p.payment_date < <cache>(('2005-07-30' + interval 1 day))))  (cost=286 rows=634) (actual time=0.0164..0.551 rows=634 loops=1)
                
                -> Single-row index lookup on c using PRIMARY (customer_id=p.customer_id)  (cost=0.25 rows=1) (actual time=554e-6..571e-6 rows=1 loops=634)

Как я понимаю из вывода время по индексированным позициям уменьшилось. 

#Задание 3.

В PostgreSQL как и в MySQL используются индексы B-TREE, HASH, а также GiST, SP-GiST, GIN, BRIN.  

