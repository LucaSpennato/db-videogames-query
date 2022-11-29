1. Selezionare i dati di tutti giocatori che hanno scritto almeno una recensione, mostrandoli una sola volta (996)
```sql
select player_id from players
JOIN reviews
	on players.id = reviews.player_id
GROUP BY player_id
```

2. Sezionare tutti i videogame dei tornei tenuti nel 2016, mostrandoli una sola volta (226)
```sql
select DISTINCT videogames.id from videogames
JOIN tournament_videogame
	on videogames.id = tournament_videogame.videogame_id
JOIN tournaments
	on tournament_videogame.tournament_id = tournaments.id
WHERE tournaments.`year` = 2016
```

3. Mostrare le categorie di ogni videogioco (1718)
```sql
select * from videogames
JOIN category_videogame
	on videogames.id = category_videogame.videogame_id
JOIN categories
	on category_videogame.category_id = categories.id
```

4. Selezionare i dati di tutte le software house che hanno rilasciato almeno un gioco dopo il 2020, mostrandoli una sola volta (6)
```sql
SELECT DISTINCT software_houses.* from software_houses
JOIN videogames
	on software_houses.id = videogames.software_house_id
WHERE YEAR(release_date) = 2020
```

5. Selezionare i premi ricevuti da ogni software house per i videogiochi che ha prodotto (55)
```sql
SELECT awards.`name`, software_houses.`name` from software_houses
JOIN videogames
	on software_houses.id = videogames.software_house_id
JOIN award_videogame
	on videogames.id = award_videogame.videogame_id
JOIN awards
	on award_videogame.award_id = awards.id
```

6. Selezionare categorie e classificazioni PEGI dei videogiochi che hanno ricevuto recensioni da 4 e 5 stelle, mostrandole una sola volta (3363)
```sql
SELECT DISTINCT videogames.name, pegi_labels.`name`, categories.name from pegi_labels
JOIN pegi_label_videogame
	on pegi_labels.id = pegi_label_videogame.pegi_label_id
JOIN videogames 
	ON pegi_label_videogame.videogame_id = videogames.id
JOIN category_videogame
	on videogames.id = category_videogame.videogame_id
JOIN categories 
	ON category_videogame.category_id = categories.id
JOIN reviews 
	ON videogames.id = reviews.videogame_id
WHERE reviews.rating >= 4 
```

7. Selezionare quali giochi erano presenti nei tornei nei quali hanno partecipato i giocatori il cui nome inizia per 'S' (474)
```sql
SELECT DISTINCT videogames.`name` from videogames
JOIN tournament_videogame
	on videogames.id = tournament_videogame.videogame_id
JOIN tournaments 
	ON tournament_videogame.tournament_id = tournaments.id
JOIN player_tournament
	on tournaments.id = player_tournament.player_id
JOIN players 
	ON player_tournament.player_id = players.id
WHERE players.`name` LIKE "s%"
-- 421
```

8. Selezionare le cittÃ  in cui Ã¨ stato giocato il gioco dell'anno del 2018 (36)
```sql
SELECT DISTINCT tournaments.city from tournaments
JOIN tournament_videogame
	on tournaments.id = tournament_videogame.tournament_id
JOIN videogames
	on tournament_videogame.videogame_id = videogames.id
JOIN award_videogame
	on videogames.id = award_videogame.videogame_id
JOIN awards
	on award_videogame.award_id
WHERE awards.`name` = "gioco dell'anno"
	and award_videogame.`year` = 2018
```

9. Selezionare i giocatori che hanno giocato al gioco piÃ¹ atteso del 2018 in un torneo del 2019 (3306)
```sql
SELECT players.* FROM players
JOIN player_tournament
	ON players.id = player_tournament.player_id
JOIN tournaments 
	ON player_tournament.tournament_id = tournaments.id
JOIN tournament_videogame
	ON tournaments.id = tournament_videogame.tournament_id
JOIN videogames 
	ON tournament_videogame.videogame_id = videogames.id
JOIN award_videogame
	on videogames.id = award_videogame.videogame_id
JOIN awards 
	ON award_videogame.award_id = awards.id
WHERE awards.`name` = "Gioco più atteso"
	AND award_videogame.`year` = 2018 
	AND tournaments.`year` = 2019
```

##### **BONUS**

10. Selezionare i dati della prima software house che ha rilasciato un gioco, assieme ai dati del gioco stesso (software house id : 5)
```sql
SELECT videogames.*, software_houses.* from software_houses
JOIN videogames
	ON software_houses.id = videogames.software_house_id
WHERE videogames.release_date = ( SELECT MIN(videogames.release_date) FROM videogames )
```

11. Selezionare i dati del videogame (id, name, release_date, totale recensioni) con piÃ¹ recensioni (videogame id : potrebbe uscire 449 o 398, sono entrambi a 20)
```sql
```

12. Selezionare la software house che ha vinto piÃ¹ premi tra il 2015 e il 2016 (software house id : potrebbe uscire 3 o 1, sono entrambi a 3)
```sql
```

13. Selezionare le categorie dei videogame i quali hanno una media recensioni inferiore a 1.5 (10)
```sql
```