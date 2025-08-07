## Задание 1 — Уникальные районы из таблицы адресов

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

### SQL-запрос:

```sql
SELECT DISTINCT district
FROM address
WHERE district LIKE 'K%a' AND district NOT LIKE '% %';

---

## Задание 2 — Фильтрация платежей

Получите из таблицы `payment` информацию по платежам, которые выполнялись в промежуток  
с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.

### SQL-запрос:

```sql
SELECT *
FROM payment
WHERE payment_date BETWEEN '2005-06-15' AND '2005-06-18'
  AND amount > 10.00;

---

## Задание 3 — последние 5 аренд

Получите последние пять аренд фильмов.

### SQL-запрос:

```sql
SELECT *
FROM rental
ORDER BY rental_date DESC
LIMIT 5;

---

## Задание 4 — выбор активных покупателей с изменёнными именами

**Условие:**
Одним запросом получить активных покупателей, имена которых Kelly или Willie,  
причём вывести имена и фамилии в нижнем регистре, а в именах заменить 'll' на 'pp'.

**SQL-запрос:**
```sql
SELECT
  LOWER(REPLACE(first_name, 'll', 'pp')) AS first_name_mod,
  LOWER(last_name) AS last_name_mod
FROM customer
WHERE active = 1
  AND first_name IN ('Kelly', 'Willie');
