# MongoDB

## overview
- stem from word Humongous
- ecosystem:
  - mongodb
  - dynamoDb
- features
  - no schema
  - nested documents (rows)
  - relation enforced manually
  - data merged and nested in a few collection
- entities
  - database
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
- clear the window: cls
- list dbs: show dbs
- use <db_name>
- db.courses.insertOne({name: "some course name"})
- db.courses.insertOne({name: "another course", prof: "someone"})
- db.courses.insertOne({name: "course 3", rate: {rate1: "1", rate2: "2", rate3: "3"}})
- db.courses.find()
- drop the collection: db.courses.drop()
- drop the db: db.dropDatabase()

## import data
- mongoimport tv-shows.json -d movieData -c movies --jsonArray --drop

## CRUD operations
- create: insertOne, insertMany
- read: findOne, find
  - find
    - db.courses.find().forEach(item => printjson(item))
  - find with filter
    - db.profs.find({age: { $gt: 50 }})
- update: updateOne
- delete: deleteOne, deleteMany
- projection: select keys in return data
  - select only name field: 
    - db.profs.find({}, {name: 1})

## data types
- text
- boolean
- number
  - Integer (int32)
  - NumberLong (int64)
  - NumberDecimal (high precision floating point)
- objectId
- ISODate
   - timestamp (internal)
- embeded document
- array

## schema modelling
- types of relation
  - reference (like traditional relation))
  - nested document
- should use embeded document
  - strong one-one relation
  - one-many relation, in which manny is a small
  - many-many, where data reflect historical record
- should use references
  - many-many, where data needs to be latest
  - one-many relation, in which manny is a lot

## db engine
- data stored as Bson
  - driver converts json to bson
  - bson supports some other types (ex. objectId())  

## create: insert, insertMany
- ordered vs non-ordered insert
  - ordered insert
    - insert one by one
    - if one fails, stop and no rollback
  - non-ordered insert
    - insert all
    - no stop if one fails
    - use this if care about inserting missing documents
- writeConcern
  - determine if write to journal needs to be confirmed
  - deternube timeout for a write
  - db.profs.insertOne({name: "leo"}, {writeConcern: {w:1, j:true}})
- atomicity
  - transcation either succeed or fail (per document level)

## network
- default port: 27017