---
layout: post
title: Designing an ETL Pipeline for a Data Warehouse
categories: [ETL,PostgreSQL,Python]
---

<img src="https://drive.google.com/thumbnail?id=1o-If_gJerhjqUZVpwmmpr8UgfNEzYnB0&sz=w640-h480"/>                                                

This was my final project for a database course, which was instructed by [Dr.Gheibi](https://scholar.google.ca/citations?user=7Eng5oAAAAAJ&hl=en).
This project had three phases:

- First, one had to design a database for a library in the fifth normal form.
- The second phase was about creating an [ETL](https://en.wikipedia.org/wiki/Extract,_transform,_load) pipeline to synchronize a data warehouse with changes in the database.
- Last but not least, one had to develop a time machine to restore the database to some time in the past.

One straightforward solution to the second part was to imitate changes operation by operation. This approach bypasses a lot of complexities, but it makes lots of overhead.

My solution was to model the database as a [DAG](https://en.wikipedia.org/wiki/Directed_acyclic_graph), meaning tables and relations were mapped to vertices and edges. Then, I used a [topological order](https://en.wikipedia.org/wiki/Topological_sorting) of this DAG to figure out the order I should apply insert, delete and update operations in bulk.

<img src="https://drive.google.com/thumbnail?id=1cSyNM637ce4potnsqWxuEe48IF1O0Viv&sz=w640-h480"/>  


In order to implement a versioning functionality in the last phase, I created one table and two views for each table in the original database. Each table in the warehouse had a column with [tstzrange](https://www.postgresql.org/docs/9.3/rangetypes.html) datatype. This column was meant to store valid time ranges for each row in the original table.


<div class="row">
  <div class="column">
    <img src="https://drive.google.com/thumbnail?id=1P0uydQYSuGgcB8vVW7iUlm8VLoeoAxTr&sz=w640-h1024"/>
  </div>
  <div class="column">
    <img src="https://drive.google.com/thumbnail?id=1OAQyrF9klAFqw8smieVGNsRMGyVxKWny&sz=w640-h480"/>
  </div>
</div>

For more details and complete source code, please check out [this](https://github.com/KooroshMoslemi/ETL-Pipeline) repository.








