# joins-subqueries-test
Data Bases September test

# Nicolás Machado da Silva
---

 #### 1 - Mostrar todos los actores que participan en películas.
```sql
SELECT actor.actor_id AS actor_id, GROUP_CONCAT(film_actor.film_id) AS films_ids
FROM actor 
INNER JOIN film_actor
ON actor.actor_id=film_actor.actor_id
GROUP BY actor.actor_id
```
 #### 2 - Mostrar la cantidad de actores que participan por película.
```sql
SELECT COUNT(*) cantidad_actores, f.title titulo_pelicula
FROM actor a 
INNER JOIN film_actor fa 
ON a.actor_id=fa.actor_id 
INNER JOIN film f ON fa.film_id=f.film_id
GROUP BY f.title;
```
#### 3 - Mostrar la cantidad de películas que participa cada actor.
```sql
SELECT actor.actor_id, actor.first_name, COUNT(*) AS films_count
FROM actor
INNER JOIN film_actor
ON actor.actor_id = film_actor.actor_id
GROUP BY actor.actor_id
```
#### 4 - Saber si hay actores que no trabajaron en ninguna película. 
```sql
SELECT a.actor_id id, a.first_name nombre
FROM actor a
LEFT JOIN film_actor fa
ON fa.actor_id = a.actor_id
WHERE fa.film_id IS NULL;
```
#### 5 - Mostrar los actores que participan en películas por arriba del promedio que el resto.
FALLA, no se puede referenciar al alias `films_count`...pero podriamos solucionarlo con alias
```sql
SELECT actor.actor_id, COUNT(film_actor.film_id) AS films_count
FROM actor
INNER JOIN film_actor
ON actor.actor_id=film_actor.actor_id
WHERE films_count >= (SELECT AVG(film.film_id) FROM actor INNER JOIN film_actor ON actor.actor_id=film_actor.actor_id)
GROUP BY actor.actor_id
```
#### 6 - Mostrar los actores que participan en películas por debajo del promedio que el resto.
```bash

```
#### 7 - Mostrar cantidad de películas por tienda.
```sql
SELECT COUNT(*) films, inventory.store_id
FROM inventory
GROUP BY inventory.store_id
```
#### 8 - Mostrar cantidad de películas por película y tienda.
```bash
SELECT COUNT(*) cantidad, f.title pelicula, i.store_id id_tienda
FROM film f
INNER JOIN inventory i
ON f.film_id=i.film_id
GROUP BY f.title, i.store_id;
```
#### 9 - Mostrar cantidad de películas por arriba del promedio del rental_rate
```bash

```

#### 10 - Mostrar cantidad de actores por película, que están por arriba del promedio en replacement_cost
