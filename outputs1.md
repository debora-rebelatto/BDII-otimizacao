Windows:

```sql
                                                                 QUERY PLAN
--------------------------------------------------------------------------------------------------------------------------------------------
 Gather  (cost=6158.20..21271.90 rows=4 width=17) (actual time=26.354..88.600 rows=66 loops=1)
   Workers Planned: 2
   Workers Launched: 2
   ->  Nested Loop  (cost=5158.20..20271.50 rows=2 width=17) (actual time=24.383..83.074 rows=22 loops=3)
         ->  Hash Join  (cost=5157.78..20270.60 rows=2 width=8) (actual time=24.359..82.765 rows=22 loops=3)
               Hash Cond: (c.person_id = p.id)
               ->  Parallel Seq Scan on casts c  (cost=0.00..13900.87 rows=461687 width=16) (actual time=0.018..31.615 rows=357412 loops=3)
               ->  Hash  (cost=5157.76..5157.76 rows=1 width=8) (actual time=23.789..23.790 rows=1 loops=3)
                     Buckets: 1024  Batches: 1  Memory Usage: 9kB
                     ->  Seq Scan on people p  (cost=0.00..5157.76 rows=1 width=8) (actual time=0.552..23.784 rows=1 loops=3)
                           Filter: (name = 'Keanu Reeves'::text)
                           Rows Removed by Filter: 267260
         ->  Index Scan using movies_pkey on movies m  (cost=0.42..0.45 rows=1 width=25) (actual time=0.012..0.012 rows=1 loops=66)
               Index Cond: (id = c.movie_id)
 Planning time: 0.957 ms
 Execution time: 88.677 ms
(16 rows)
```
