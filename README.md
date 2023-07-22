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

SELECT DATE_FORMAT(payment_date, '%M – %Y'), COUNT(r.rental_id), SUM(amount)

from payment p

join rental r on r.rental_id = p.rental_id

GROUP BY DATE_FORMAT(payment_date, '%M – %Y')

ORDER BY SUM(amount) DESC LIMIT 1;

![VirtualBox_Debian11-master_22_07_2023_17_34_20](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/3f4ecabb-761c-427a-b4c9-e5f95be94d1b)



#Задание 4.

SELECT staff_id, COUNT(payment_id),

CASE

WHEN count(payment_id) > 8000 THEN 'Да'

WHEN COUNT(payment_id) < 8000 THEN 'Нет'

ELSE 'Average user'

END AS Премия

FROM payment p 

GROUP BY staff_id

ORDER BY COUNT(payment_id) DESC

LIMIT 5;

![VirtualBox_Debian11-master_22_07_2023_12_47_54](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/40d56ec2-9dbf-441d-a4eb-6834f4d205e4)

 
#Задание 5.

SELECT f.title

FROM film f

LEFT JOIN inventory i ON i.film_id = f.film_id

LEFT JOIN rental r ON r.inventory_id = i.inventory_id

WHERE r.rental_id IS NULL;

![VirtualBox_Debian11-master_22_07_2023_13_40_27](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/e0a5487a-e908-4c4b-b191-847589d9dc7d)

