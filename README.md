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

-> Limit: 200 row(s)  (actual time=10.7..10.7 rows=200 loops=1)

    -> Table scan on <temporary>  (actual time=10.7..10.7 rows=200 loops=1)
    
        -> Aggregate using temporary table  (actual time=10.7..10.7 rows=391 loops=1)
        
            -> Nested loop inner join  (cost=5596 rows=15813) (actual time=0.0875..10.3 rows=634 loops=1)
            
                -> Table scan on c  (cost=61.2 rows=599) (actual time=0.0307..0.148 rows=599 loops=1)
                
                -> Filter: (cast(p.payment_date as date) = '2005-07-30')  (cost=6.6 rows=26.4) (actual time=0.0153..0.0169 rows=1.06 loops=599)
                
                    -> Index lookup on p using idx_fk_customer_id (customer_id=c.customer_id)  (cost=6.6 rows=26.4) (actual time=0.0133..0.0155 rows=26.8 loops=599

Добавлены индексы payment_data и amount.

CREATE INDEX data_amount ON payment(payment_date, amount);
![VirtualBox_Debian11-master_24_07_2023_11_23_32](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/6d3120d0-5a4a-4d10-96f9-7f52eb9b7b49)

# Explain analyze Запроса после индексации

Limit: 200 row(s)  (actual time=11.8..11.8 rows=200 loops=1)

    -> Table scan on <temporary>  (actual time=11.8..11.8 rows=200 loops=1)
    
        -> Aggregate using temporary table  (actual time=11.8..11.8 rows=391 loops=1)
        
            -> Nested loop inner join  (cost=5596 rows=15813) (actual time=0.109..11.4 rows=634 loops=1)
            
                -> Table scan on c  (cost=61.2 rows=599) (actual time=0.0351..0.153 rows=599 loops=1)
                
                -> Filter: (cast(p.payment_date as date) = '2005-07-30')  (cost=6.6 rows=26.4) (actual time=0.0168..0.0187 rows=1.06 loops=599)
                
                    -> Index lookup on p using idx_fk_customer_id (customer_id=c.customer_id)  (cost=6.6 rows=26.4) (actual time=0.0147..0.0172 rows=26.8 loops=599)
                    

После индексации время на выполнение потребовалось больше, стоимость запроса не изменилась.

Менял индексацию, время увеличивалось, даже после удаления индексов время выполнения какждый раз возрастает.

Индексации в данном случае не требуется. 

#Задание 3.

В PostgreSQL как и в MySQL используются индексы B-TREE, HASH, а также GiST, SP-GiST, GIN, BRIN.  

