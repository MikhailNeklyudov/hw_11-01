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


#Задание 3.



