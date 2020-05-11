---
layout: note
title: Non-trivial SQL queries
category: DB
---

# Deleting from a table using a join
``` sql
delete r from readings r
join registers on r.registerId=registers.id
join meters on registers.meterId=meters.id
where meters.id=71
```

# Calculating Percentage in total in each group
``` sql
select count(id) as Count, category, sum(count(*)) over () as Total, 
100.0*count(id)/sum(count(*)) over () as Percentage from Items     
group by category
```