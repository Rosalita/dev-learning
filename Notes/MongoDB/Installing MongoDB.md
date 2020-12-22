# Installing MongoDB
#mongodb 

### Windows 7
MonogoDB 4.4 community edition removes support for Windows 7, 
Version 4.2.11 should still be Windows 7 Compatible.

### Windows 10
Download [MongoDB Community Server](https://www.mongodb.com/try/download/community)

MongoDB Shell is included as part of the server installation.

Mongod server must be running before it can be connected to with Mongo shell. The MongoDB service will be started upon successful installation.

Can then navigate to `C:\Program Files\MongoDB\Server\4.4\bin` abd double click mongo.exe to run the shell.

To test everything is working type `show dbs` this should list all databases.

Next add Mongo's bin folder to the `Path` environment variable.

Then can start Mongo Shell with `mongo`

