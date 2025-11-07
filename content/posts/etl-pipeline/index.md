---
title: "Designing an ETL Pipeline for a Data Warehouse"
date: 2021-11-13T00:00:00+00:00
description: "A three-phase project for a database course, including database design, ETL pipeline creation, and a 'time machine' feature for database restoration."
author:
  name: "Koorosh Moslemi"
  image: "images/author/john.png"
categories:
  - "ETL"
  - "PostgreSQL"
  - "Python"
tags:
  - "ETL"
  - "PostgreSQL"
  - "Python"
  - "Database"
  - "Data Warehouse"
hero: "etl.png"
menu:
  sidebar:
    name: "ETL Pipeline"
    identifier: "etl-pipeline"
    weight: 40
---

This project was my final submission for a database course instructed by [Dr. Gheibi](https://scholar.google.ca/citations?user=7Eng5oAAAAAJ&hl=en). The project was divided into three main phases:

1.  **Database Design**: The first phase required designing a database for a library, ensuring it adhered to the fifth normal form (5NF).
2.  **ETL Pipeline**: The second phase involved creating an [ETL (Extract, Transform, Load)](https://en.wikipedia.org/wiki/Extract,_transform,_load) pipeline to synchronize a data warehouse with the operational database.
3.  **Time Machine**: The final phase was to develop a "time machine" feature that could restore the database to a specific point in the past.

For the ETL pipeline, a common approach is to replicate each database operation individually, but this can create significant overhead. Instead, I modeled the database as a [Directed Acyclic Graph (DAG)](https://en.wikipedia.org/wiki/Directed_acyclic_graph), where tables and their relationships were represented as vertices and edges. I then used a [topological sort](https://en.wikipedia.org/wiki/Topological_sorting) of this DAG to determine the optimal order for applying bulk insert, delete, and update operations.

{{< img src="https://drive.google.com/thumbnail?id=1cSyNM637ce4potnsqWxuEe48IF1O0Viv&sz=w640-h480" title="Database as DAG" align="center" >}}

To implement the versioning functionality for the "time machine," I created a table and two views for each table in the original database. Each table in the data warehouse included a column with the `tstzrange` datatype to store the valid time ranges for each row.


<div class="row">
  <div class="row">
    {{< img src="https://drive.google.com/thumbnail?id=1OAQyrF9klAFqw8smieVGNsRMGyVxKWny&sz=w640-h480" align="center" title="Versioning 2" >}}
  </div>
  <div class="row">
    {{< img src="https://drive.google.com/thumbnail?id=1P0uydQYSuGgcB8vVW7iUlm8VLoeoAxTr&sz=w1024-h768" align="center" title="Versioning 1" >}}
  </div>
</div>
<!-- {{< split 6 6 >}}
  {{< img src="https://drive.google.com/thumbnail?id=1P0uydQYSuGgcB8vVW7iUlm8VLoeoAxTr&sz=w640-h1024" title="Versioning 1" >}}
---
  {{< img src="https://drive.google.com/thumbnail?id=1OAQyrF9klAFqw8smieVGNsRMGyVxKWny&sz=w640-h480" title="Versioning 2" >}}
{{< /split >}} -->

For more details and the complete source code, please visit the [project repository](https://github.com/KooroshMoslemi/ETL-Pipeline).
