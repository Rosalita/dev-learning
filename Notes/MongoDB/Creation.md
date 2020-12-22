# Creation
#mongodb 

Mongo creates when it saves for the first time.

Mongo creates a database when you first store data in it.

Mongo will create a collection when you first store data for that collection.

There isn't a `create` command in MongoDB Shell. To create a new database you use the `use` command. If the database doesn't exist, then MongoDB will create it. 

To add [[Documents]] to a database, use the `db.<collection>.insert` command. 

> db.rosie.insert({date:"21/12/2020", task:"started learning mongo"})
> WriteResult({ "nInserted" : 1 })

