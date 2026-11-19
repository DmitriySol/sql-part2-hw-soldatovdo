# Домашнее задание к занятию «SQL. Часть 2» - Солдатов Дмитрий

## Задание 1

**Запрос:**
~~~sql
SELECT 
    s.first_name AS 'Имя сотрудника',
    s.last_name AS 'Фамилия сотрудника',
    ci.city AS 'Город магазина',
    COUNT(c.customer_id) AS 'Количество покупателей'
FROM store st
JOIN staff s ON st.store_id = s.store_id
JOIN address a ON st.address_id = a.address_id
JOIN city ci ON a.city_id = ci.city_id
JOIN customer c ON st.store_id = c.store_id
GROUP BY s.first_name, s.last_name, ci.city
HAVING COUNT(c.customer_id) > 300;
~~~

**Результат:**
<img width="1239" height="233" alt="image" src="https://github.com/user-attachments/assets/c8b61f18-2945-43bb-8ee8-3f49f69bab30" />


---

## Задание 2

**Запрос:**
~~~sql
SELECT COUNT(*) AS 'Количество фильмов'
FROM film
WHERE length > (SELECT AVG(length) FROM film);
~~~

**Результат:**
<img width="851" height="167" alt="image" src="https://github.com/user-attachments/assets/4ea337e8-1ae8-4429-83db-d6e0e674b8db" />


---

## Задание 3

**Запрос:**
~~~sql
SELECT 
    DATE_FORMAT(p.payment_date, '%Y-%m') AS 'Месяц',
    SUM(p.amount) AS 'Сумма платежей',
    COUNT(r.rental_id) AS 'Количество аренд'
FROM payment p
JOIN rental r ON p.rental_id = r.rental_id
GROUP BY DATE_FORMAT(p.payment_date, '%Y-%m')
ORDER BY SUM(p.amount) DESC
LIMIT 1;
~~~

**Результат:**
<img width="1010" height="175" alt="image" src="https://github.com/user-attachments/assets/b7a5b691-1c42-43d0-aa31-56f1465a1503" />

