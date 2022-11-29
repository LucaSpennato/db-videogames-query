## Select `
1.  Selezionare tutte le software house americane (3)
```sql 
select * from software_houses
    where country = "united states"
```

2. Selezionare tutti i giocatori della cittÃ di 'Rogahnland' (2)
```sql
select * from players
    where city = "rogahnland"
```

3. Selezionare tutti i giocatori il cui nome finisce per "a" (220)
```sql 
select * from players
where name LIKE "%a"
```

4.  Selezionare tutte le recensioni scritte dal giocatore con ID = 800 (11)
```sql
select * from reviews
where player_id = 800
```

5. Contare quanti tornei ci sono stati nell'anno 2015 (9)
```sql
select COUNT(*) from tournaments
where year = 2015
```

6. Selezionare tutti i premi che contengono nella descrizione la parola 'facere' (2)
```sql
select * from awards
where description LIKE "%facere%"
```

7. Selezionare tutti i videogame che hanno la categoria 2 (FPS) o 6 (RPG), mostrandoli una sola volta (del videogioco vogliamo solo l'ID) (287)
```sql
SELECT DISTINCT videogame_id from category_videogame
where category_id = 2 OR category_id = 6
```

8. Selezionare tutte le recensioni con voto compreso tra 2 e 4 (2947)
```sql
select * from reviews
where rating BETWEEN 2 and 4
```

9. Selezionare tutti i dati dei videogiochi rilasciati nell'anno 2020 (46)
```sql
select * from videogames
where year(release_date) = "2020" 
```

10. Selezionare gli id dei videogame che hanno ricevuto almeno una recensione da stelle, mostrandoli una sola volta (443)
```sql
select distinct videogame_id from reviews
where rating = 5
```

### Bonus

11. Selezionare il numero e la media delle recensioni per il videogioco con ID = 412 (review number = 12, avg_rating = 3.16 circa)
```sql
select count(rating), AVG(rating)
from reviews
where videogame_id = 412
```

12. Selezionare il numero di videogame che la software house con ID = 1 ha rilasciato nel 2018 (13)
```sql
select COUNT(*) from videogames
where software_house_id = 1 
	and YEAR(release_date) = 2018
```