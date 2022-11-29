1. Contare quante software house ci sono per ogni paese (3)
```sql
SELECT *, COUNT(id) from software_houses
GROUP BY country
```

2. Contare quante recensioni ha ricevuto ogni videogioco (del videogioco vogliamo solo l'ID) (500)
```sql
SELECT videogame_id ,COUNT(*) FROM reviews
GROUP BY videogame_id
```

3. Contare quanti videogiochi hanno ciascuna classificazione PEGI (della classificazione PEGI vogliamo solo l'ID) (13)
```sql
select videogame_id from pegi_label_videogame
GROUP BY pegi_label_id
```

4. Mostrare il numero di videogiochi rilasciati ogni anno (11)
```sql
select count(*) from videogames
group BY year(release_date)
```

5. Contare quanti videogiochi sono disponbiili per ciascun device (del device vogliamo solo l'ID) (7)
```sql
select videogame_id from device_videogame
group BY device_id
```

6. Ordinare i videogame in base alla media delle recensioni (del videogioco vogliamo solo l'ID) (500)
```sql
select id from reviews
GROUP BY videogame_id
```