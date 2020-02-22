# MongoDB

## overview
- ecosystem:
  - mongodb
  - dynamoDb
- stem from word Humongous
- features
  - no schema
  - relation enforced manually
  - data merged and nested in a few collection
- entities
  - table: collection
  - row: document
  - column: fields
- pros 
  - fast query
  - flexible schema
  - less relation merge
- cons
  - duplicate data (messy data)

## installation
- docker run --name mongoServer -d mongo:latest

## connect to mongo via docker
- docker exec -it mongoContainer mongo

## CLI
- show dbs
- use <db_name>
- db.courses.insertOne({name: "some course name"})
- db.courses.insertOne({name: "another course", prof: "someone"})
- db.courses.insertOne({name: "course 3", rate: {rate1: "1", rate2: "2", rate3: "3"}})
- db.courses.find()