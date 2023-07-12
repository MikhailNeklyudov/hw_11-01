# Домашнее задание SQL.Часть1-Неклюдов Михаил


#Задание 1.

SELECT DISTINCT district

from address

WHERE district LIKE 'K%a' and district NOT LIKE '% %';

![Задание 1](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/15f27570-cabf-4889-8d8a-0f19a766c92e)


#Задание 2.

SELECT *, CAST(payment_date as DATE) 

FROM payment

WHERE CAST(payment_date as DATE) BETWEEN '2005-06-15' AND '2005-06-18'  AND amount > 10;

![Задание 2](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/7e36a381-ed75-47a3-ab45-64a8d71017a3)


#Задание 3.

SELECT *

FROM rental r

order by rental_id DESC

limit 5;

![Задание 3](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/d398b6ba-92eb-43b4-a8b7-5adfc4d9dd5c)


#Задание 4.

SELECT LOWER(first_name), LOWER(last_name), LOWER(REPLACE(first_name, 'LL', 'pp')) 

FROM customer

WHERE first_name = 'Kelly' OR first_name = 'Willie';

![задание 4](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/e05629a0-578e-426f-9edc-51b474863c49)


#Задание 5.

SELECT SUBSTRING_INDEX(email, '@', 1), SUBSTRING_INDEX(email, '@', -1)

from customer;

![задание 5](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/708afff1-b2ab-4a17-bfbf-67ab5560a3c7)


#Задание 6.


Не получилось сделать. 
