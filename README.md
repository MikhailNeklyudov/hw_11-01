# Домашнее задание SQL.Часть2-Неклюдов Михаил


#Задание 1.

ELECT CONCAT(s.first_name, ' ', s.last_name) as Фамилия_имя_сотрудника_магазина, Количество_покупателей, c2.city as Город

FROM staff s

Left join address a on a.address_id = s.address_id

LEFT JOIN city c2 on c2.city_id = a.city_id 

JOIN (

SELECT store_id, COUNT(customer_id) AS Количество_покупателей

FROM customer c

GROUP BY store_id) t1 ON s.store_id = t1.store_id

HAVING Количество_покупателей > 300;

![VirtualBox_Debian11-master_21_07_2023_14_43_46](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/10ca0df1-e1cd-4d76-9cb1-38e3a3186a88)


#Задание 2.

SELECT COUNT(film_id) 

from film f

WHERE length > (SELECT AVG(length) from film);


![VirtualBox_Debian11-master_21_07_2023_12_29_44](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/90002d0e-aaea-471a-81f1-3c183ac4766d)


#Задание 3.

SELECT MONTHNAME(payment_date), COUNT(r.rental_id), SUM(amount) 

from payment p

join rental r on r.rental_id = p.rental_id 

GROUP BY MONTHNAME(payment_date);

![VirtualBox_Debian11-master_22_07_2023_07_09_47](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/df0199f1-6e3c-4f5e-afec-906ceb05bc3d)



#Задание 4.


 
#Задание 5.

