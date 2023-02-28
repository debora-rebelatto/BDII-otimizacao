# Query 1: Com Index

1-

```sql
omdb=# EXPLAIN ANALYZE SELECT m.name
FROM movies m
JOIN casts c ON m.id = c.movie_id
JOIN people p ON c.person_id = p.id
WHERE p.name = 'Keanu Reeves';
                                                                 QUERY PLAN
---------------------------------------------------------------------------------------------------------------------------------------------
 Nested Loop  (cost=1.27..75.17 rows=4 width=17) (actual time=0.020..0.193 rows=66 loops=1)
   ->  Nested Loop  (cost=0.85..73.37 rows=4 width=8) (actual time=0.016..0.057 rows=66 loops=1)
         ->  Index Scan using idx_people_name on people p  (cost=0.42..8.44 rows=1 width=8) (actual time=0.010..0.010 rows=1 loops=1)
               Index Cond: (name = 'Keanu Reeves'::text)
         ->  Index Scan using idx_casts_person_id on casts c  (cost=0.43..64.76 rows=17 width=16) (actual time=0.004..0.040 rows=66 loops=1)
               Index Cond: (person_id = p.id)
   ->  Index Scan using idx_movies_id on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.002..0.002 rows=1 loops=66)
         Index Cond: (id = c.movie_id)
 Planning Time: 0.313 ms
 Execution Time: 0.209 ms
(10 rows)
```

2-

```sql
omdb=# EXPLAIN ANALYZE SELECT m.name
FROM movies m
JOIN casts c ON m.id = c.movie_id
JOIN people p ON c.person_id = p.id
WHERE p.name = 'Keanu Reeves';
                                                                 QUERY PLAN
---------------------------------------------------------------------------------------------------------------------------------------------
 Nested Loop  (cost=1.27..75.17 rows=4 width=17) (actual time=0.028..0.356 rows=66 loops=1)
   ->  Nested Loop  (cost=0.85..73.37 rows=4 width=8) (actual time=0.022..0.093 rows=66 loops=1)
         ->  Index Scan using idx_people_name on people p  (cost=0.42..8.44 rows=1 width=8) (actual time=0.013..0.014 rows=1 loops=1)
               Index Cond: (name = 'Keanu Reeves'::text)
         ->  Index Scan using idx_casts_person_id on casts c  (cost=0.43..64.76 rows=17 width=16) (actual time=0.006..0.065 rows=66 loops=1)
               Index Cond: (person_id = p.id)
   ->  Index Scan using idx_movies_id on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.003..0.003 rows=1 loops=66)
         Index Cond: (id = c.movie_id)
 Planning Time: 0.475 ms
 Execution Time: 0.387 ms
(10 rows)
```

3-

```sql
omdb=# EXPLAIN ANALYZE SELECT m.name
FROM movies m
JOIN casts c ON m.id = c.movie_id
JOIN people p ON c.person_id = p.id
WHERE p.name = 'Keanu Reeves';
                                                                 QUERY PLAN
---------------------------------------------------------------------------------------------------------------------------------------------
 Nested Loop  (cost=1.27..75.17 rows=4 width=17) (actual time=0.022..0.270 rows=66 loops=1)
   ->  Nested Loop  (cost=0.85..73.37 rows=4 width=8) (actual time=0.017..0.073 rows=66 loops=1)
         ->  Index Scan using idx_people_name on people p  (cost=0.42..8.44 rows=1 width=8) (actual time=0.011..0.011 rows=1 loops=1)
               Index Cond: (name = 'Keanu Reeves'::text)
         ->  Index Scan using idx_casts_person_id on casts c  (cost=0.43..64.76 rows=17 width=16) (actual time=0.004..0.048 rows=66 loops=1)
               Index Cond: (person_id = p.id)
   ->  Index Scan using idx_movies_id on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.002..0.002 rows=1 loops=66)
         Index Cond: (id = c.movie_id)
 Planning Time: 0.431 ms
 Execution Time: 0.294 ms
(10 rows)
```

4-

```sql
omdb=# EXPLAIN ANALYZE SELECT m.name
 FROM movies m
JOIN casts c ON m.id = c.movie_id
JOIN people p ON c.person_id = p.id
WHERE p.name = 'Keanu Reeves';
                                                                 QUERY PLAN
---------------------------------------------------------------------------------------------------------------------------------------------
 Nested Loop  (cost=1.27..75.17 rows=4 width=17) (actual time=0.023..0.274 rows=66 loops=1)
   ->  Nested Loop  (cost=0.85..73.37 rows=4 width=8) (actual time=0.018..0.075 rows=66 loops=1)
         ->  Index Scan using idx_people_name on people p  (cost=0.42..8.44 rows=1 width=8) (actual time=0.011..0.012 rows=1 loops=1)
               Index Cond: (name = 'Keanu Reeves'::text)
         ->  Index Scan using idx_casts_person_id on casts c  (cost=0.43..64.76 rows=17 width=16) (actual time=0.005..0.049 rows=66 loops=1)
               Index Cond: (person_id = p.id)
   ->  Index Scan using idx_movies_id on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.002..0.002 rows=1 loops=66)
         Index Cond: (id = c.movie_id)
 Planning Time: 0.447 ms
 Execution Time: 0.298 ms
(10 rows)
```

5-

```sql
omdb=# EXPLAIN ANALYZE SELECT m.name
 FROM movies m
JOIN casts c ON m.id = c.movie_id
JOIN people p ON c.person_id = p.id
WHERE p.name = 'Keanu Reeves';
                                                                 QUERY PLAN
---------------------------------------------------------------------------------------------------------------------------------------------
 Nested Loop  (cost=1.27..75.17 rows=4 width=17) (actual time=0.020..0.194 rows=66 loops=1)
   ->  Nested Loop  (cost=0.85..73.37 rows=4 width=8) (actual time=0.016..0.059 rows=66 loops=1)
         ->  Index Scan using idx_people_name on people p  (cost=0.42..8.44 rows=1 width=8) (actual time=0.010..0.010 rows=1 loops=1)
               Index Cond: (name = 'Keanu Reeves'::text)
         ->  Index Scan using idx_casts_person_id on casts c  (cost=0.43..64.76 rows=17 width=16) (actual time=0.004..0.041 rows=66 loops=1)
               Index Cond: (person_id = p.id)
   ->  Index Scan using idx_movies_id on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.002..0.002 rows=1 loops=66)
         Index Cond: (id = c.movie_id)
 Planning Time: 0.317 ms
 Execution Time: 0.211 ms
(10 rows)
```
