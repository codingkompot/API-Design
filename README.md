# API-Design

## Consider the type of data we will be storing and therefore the type of database we should implement

### People.csv -
personId, name, age, houseid
4, “Sally”, 47, 136

### Houses.csv -
Houseid, address, ownerid, no_of_people_in_hh, neighbourhoodid
136, “123 TreeHouse Lane”, 4, 3, 72

### Addresses.csv -
Neighbourhoodid, postcode, address
72, “SE11 7GH”, “123 Treehouse Lane”

## We would be storing CSV data and we would be using Sql for the purpose of using relational databases.

### Schema for this Database

Table People {
 personid PK // auto-increment
 name CharField
 age IntegerField
 houseid ForeignKey [ref: > Houses.houseid]
}
Table Houses {
 houseid PK // auto-increment
 address CharField
 no_of_people_in_hh IntegerField
 ownerid ForeignKey [ref: > People.personid]
 neighbourhoodid ForeignKey [ref: > Addresses.neighbourhoodid]
}
Table Addresses {
 neighbourhoodid PK // auto-increment
 postcode CharField
 address CharField [ref: > Houses.address]
}

### Picture of Schema



## Consider the requests our API should be capable of handling

GET - for reading data
POST - for inserting new data
PUT/PATCH - for updating pre-existing data
DELETE - delete a record

### List the routes you will need with their HTTP verb and path

http://localhost:3000/api/people/:id

SELECT name, houseid FROM people WHERE personID = 4;

GET

http://localhost:3000/api/people/new

This would be our URL for our POST requests.
