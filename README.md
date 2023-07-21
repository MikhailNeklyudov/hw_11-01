# Домашнее задание SQL.Часть2-Неклюдов Михаил


#Задание 1.

SELECT CONCAT(s.first_name, ' ', s.last_name) as Фамилия_имя_сотрудника_магазина, Количество_покупателей

FROM staff s

JOIN (

SELECT store_id, COUNT(customer_id) AS Количество_покупателей

FROM customer c

GROUP BY store_id) t1 ON s.store_id = t1.store_id

HAVING Количество_покупателей > 300;

![VirtualBox_Debian11-master_21_07_2023_12_51_46](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/0821aabd-6f7f-4700-91b4-b0c5ac830ee7)


#Задание 2.

SELECT COUNT(film_id) 

from film f

WHERE length > (SELECT AVG(length) from film);


![VirtualBox_Debian11-master_21_07_2023_12_29_44](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/90002d0e-aaea-471a-81f1-3c183ac4766d)


#Задание 3.



#Задание 4.


 
#Задание 5.

