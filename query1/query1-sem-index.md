# Query 1 - Sem Index

1-

```sql
                                                                 QUERY PLAN
--------------------------------------------------------------------------------------------------------------------------------------------
 Gather  (cost=4792.37..19974.33 rows=4 width=17) (actual time=19.946..105.471 rows=66 loops=1)
   Workers Planned: 2
   Workers Launched: 2
   ->  Nested Loop  (cost=3792.37..18973.93 rows=2 width=17) (actual time=15.564..97.995 rows=22 loops=3)
         ->  Parallel Hash Join  (cost=3791.95..18973.02 rows=2 width=8) (actual time=15.500..97.317 rows=22 loops=3)
               Hash Cond: (c.person_id = p.id)
               ->  Parallel Seq Scan on casts c  (cost=0.00..13963.66 rows=463766 width=16) (actual time=0.076..46.040 rows=359062 loops=3)
               ->  Parallel Hash  (cost=3791.94..3791.94 rows=1 width=8) (actual time=13.328..13.329 rows=0 loops=3)
                     Buckets: 1024  Batches: 1  Memory Usage: 40kB
                     ->  Parallel Seq Scan on people p  (cost=0.00..3791.94 rows=1 width=8) (actual time=8.323..13.254 rows=0 loops=3)
                           Filter: (name = 'Keanu Reeves'::text)
                           Rows Removed by Filter: 89304
         ->  Index Scan using movies_pkey on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.028..0.029 rows=1 loops=66)
               Index Cond: (id = c.movie_id)
 Planning Time: 1.220 ms
 Execution Time: 105.604 ms
(16 rows)

```

2 -

```sql
                                                                 QUERY PLAN
--------------------------------------------------------------------------------------------------------------------------------------------
 Gather  (cost=4792.37..19974.33 rows=4 width=17) (actual time=15.403..154.434 rows=66 loops=1)
   Workers Planned: 2
   Workers Launched: 2
   ->  Nested Loop  (cost=3792.37..18973.93 rows=2 width=17) (actual time=13.843..86.755 rows=22 loops=3)
         ->  Parallel Hash Join  (cost=3791.95..18973.02 rows=2 width=8) (actual time=13.814..86.524 rows=22 loops=3)
               Hash Cond: (c.person_id = p.id)
               ->  Parallel Seq Scan on casts c  (cost=0.00..13963.66 rows=463766 width=16) (actual time=0.047..37.306 rows=359062 loops=3)
               ->  Parallel Hash  (cost=3791.94..3791.94 rows=1 width=8) (actual time=11.681..11.682 rows=0 loops=3)
                     Buckets: 1024  Batches: 1  Memory Usage: 40kB
                     ->  Parallel Seq Scan on people p  (cost=0.00..3791.94 rows=1 width=8) (actual time=7.157..11.513 rows=0 loops=3)
                           Filter: (name = 'Keanu Reeves'::text)
                           Rows Removed by Filter: 89304
         ->  Index Scan using movies_pkey on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.009..0.009 rows=1 loops=66)
               Index Cond: (id = c.movie_id)
 Planning Time: 0.293 ms
 Execution Time: 154.472 ms
(16 rows)


```

3 -

```sql
                                                                 QUERY PLAN
--------------------------------------------------------------------------------------------------------------------------------------------
 Gather  (cost=4792.37..19974.33 rows=4 width=17) (actual time=14.668..93.238 rows=66 loops=1)
   Workers Planned: 2
   Workers Launched: 2
   ->  Nested Loop  (cost=3792.37..18973.93 rows=2 width=17) (actual time=12.153..85.552 rows=22 loops=3)
         ->  Parallel Hash Join  (cost=3791.95..18973.02 rows=2 width=8) (actual time=12.111..85.288 rows=22 loops=3)
               Hash Cond: (c.person_id = p.id)
               ->  Parallel Seq Scan on casts c  (cost=0.00..13963.66 rows=463766 width=16) (actual time=0.031..37.369 rows=359062 loops=3)
               ->  Parallel Hash  (cost=3791.94..3791.94 rows=1 width=8) (actual time=10.357..10.358 rows=0 loops=3)
                     Buckets: 1024  Batches: 1  Memory Usage: 40kB
                     ->  Parallel Seq Scan on people p  (cost=0.00..3791.94 rows=1 width=8) (actual time=6.305..10.282 rows=0 loops=3)
                           Filter: (name = 'Keanu Reeves'::text)
                           Rows Removed by Filter: 89304
         ->  Index Scan using movies_pkey on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.010..0.010 rows=1 loops=66)
               Index Cond: (id = c.movie_id)
 Planning Time: 0.265 ms
 Execution Time: 93.279 ms
(16 rows)
```

4-

```sql
                                                                 QUERY PLAN
--------------------------------------------------------------------------------------------------------------------------------------------
 Gather  (cost=4792.37..19974.33 rows=4 width=17) (actual time=15.938..92.127 rows=66 loops=1)
   Workers Planned: 2
   Workers Launched: 2
   ->  Nested Loop  (cost=3792.37..18973.93 rows=2 width=17) (actual time=13.194..86.203 rows=22 loops=3)
         ->  Parallel Hash Join  (cost=3791.95..18973.02 rows=2 width=8) (actual time=13.171..85.970 rows=22 loops=3)
               Hash Cond: (c.person_id = p.id)
               ->  Parallel Seq Scan on casts c  (cost=0.00..13963.66 rows=463766 width=16) (actual time=0.072..36.233 rows=359062 loops=3)
               ->  Parallel Hash  (cost=3791.94..3791.94 rows=1 width=8) (actual time=11.429..11.430 rows=0 loops=3)
                     Buckets: 1024  Batches: 1  Memory Usage: 40kB
                     ->  Parallel Seq Scan on people p  (cost=0.00..3791.94 rows=1 width=8) (actual time=7.068..11.414 rows=0 loops=3)
                           Filter: (name = 'Keanu Reeves'::text)
                           Rows Removed by Filter: 89304
         ->  Index Scan using movies_pkey on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.009..0.009 rows=1 loops=66)
               Index Cond: (id = c.movie_id)
 Planning Time: 0.257 ms
 Execution Time: 92.163 ms
(16 rows)

```

5-

```sql
                                                                 QUERY PLAN
--------------------------------------------------------------------------------------------------------------------------------------------
 Gather  (cost=4792.37..19974.33 rows=4 width=17) (actual time=15.061..92.067 rows=66 loops=1)
   Workers Planned: 2
   Workers Launched: 2
   ->  Nested Loop  (cost=3792.37..18973.93 rows=2 width=17) (actual time=13.160..86.074 rows=22 loops=3)
         ->  Parallel Hash Join  (cost=3791.95..18973.02 rows=2 width=8) (actual time=13.135..85.866 rows=22 loops=3)
               Hash Cond: (c.person_id = p.id)
               ->  Parallel Seq Scan on casts c  (cost=0.00..13963.66 rows=463766 width=16) (actual time=0.034..36.625 rows=359062 loops=3)
               ->  Parallel Hash  (cost=3791.94..3791.94 rows=1 width=8) (actual time=11.404..11.404 rows=0 loops=3)
                     Buckets: 1024  Batches: 1  Memory Usage: 40kB
                     ->  Parallel Seq Scan on people p  (cost=0.00..3791.94 rows=1 width=8) (actual time=7.021..11.342 rows=0 loops=3)
                           Filter: (name = 'Keanu Reeves'::text)
                           Rows Removed by Filter: 89304
         ->  Index Scan using movies_pkey on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.008..0.008 rows=1 loops=66)
               Index Cond: (id = c.movie_id)
 Planning Time: 0.257 ms
 Execution Time: 92.105 ms
(16 rows)

```
