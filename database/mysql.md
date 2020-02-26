## SQL

## Overview
- ecosystem
  - MySql
  - PSql
- entities
  - table: table
  - row: records
  - column: fields
- features
  - strong schema
   - fields has to be normalized
  - data distributed across multiple tables
  - connected through relations
- scaling
  - horitontal: difficult / impossible
  - vertical: possible
- pros
  - predictable
- cons
  - frequent read of complex relation is slow

## installation
- run mysql docker container
  - docker run --name mysql -e MYSQL_ROOT_PASSWORD=921021 -d -p 3306:3306 -v mysql_data:/var/lib/mysql/data mysql:5.7

- run psql docker container
  - docker run --name postgres -e POSTGRES_PASSWORD=921021 -d -p 5432:5432 -v postgres_data:/var/lib/postgresql/data postgres

## SQL syntax
- SELECT, FROM, and WHERE
- join (aka inner join)
- left join (aka left outer join)
- right join (aka right outer join)
- full join (aka full outer join)
- cross join

## questions
- What are indexes and how do they work?
- Model me a “many to many” relationship.
- What is the difference between = NULL and IS NULL?
- What’s a prepared statement and why do we use them?


