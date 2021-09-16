# joins-subqueries-test
Data Bases September test

# Nicolás Machado da Silva
---

 #### Mostrar todos los actores que participan en películas.
```sql
SELECT actor.actor_id AS actor_id, GROUP_CONCAT(film_actor.film_id) AS films_ids
FROM actor 
INNER JOIN film_actor
ON actor.actor_id=film_actor.actor_id
GROUP BY actor.actor_id
```
 #### Mostrar la cantidad de actores que participan por película.
```sql
select a.first_name, count(*) number_of_movies
from actor a
inner join film_actor fa
on a.actor_id = fa.actor_id
GROUP by a.first_name;
```
#### Mostrar la cantidad de películas que participa cada actor.
```sql
select f.title, count(*) number_of_actors
from film f
inner join film_actor fa
on f.film_id = fa.film_id
group by f.title;
```
#### Saber si hay actores que no trabajaron en ninguna película. 
```sql
SELECT a.actor_id
FROM actors a
LEFT JOIN film_actor fa
ON fa.film_id = a.film_id
WHERE fa.film_id IS NULL
```
#### Mostrar los actores que participan en películas por arriba del promedio que el resto.
```sql
# TO REFACTOR

SELECT * FROM actor WHERE
(
SELECT actor.actor_id, COUNT(*) 
    INNER JOIN film_actor fa
    ON actor.actor_id = fa.actor_id 
    >
    (
    SELECT AVG(count_actor) FROM
	(
		SELECT COUNT(*) count_actor
		FROM film f
		INNER JOIN film_actor fa
		on fa.film_id = f.film_id
		GROUP by fa.actor_id
	) 
        AS l;
    )
)
```
#### Mostrar los actores que participan en películas por debajo del promedio que el resto.
```bash

```
#### Mostrar cantidad de películas por tienda.
```bash

```
#### Mostrar cantidad de películas por película y tienda.
```bash

```
#### Mostrar cantidad de películas por arriba del promedio del rental_rate
```bash

```

#### Mostrar cantidad de actores por película, que están por arriba del promedio en replacement_cost
