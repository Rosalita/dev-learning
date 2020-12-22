# Naming Conventions
#mongodb

## Databases
- Try to name the database after the project and only have one database per project.
- Database names can't be more than 64 bytes. 4 base64 characters can fit into 3 bytes of data. so around 84 characters would fit into 64 bytes.
- Database names can't contain / \ . " * < > : | ? $ a single space or a null character.
- Database names are case-sensitive, even on non-case sensitive file systems. So keep them lower case.

## Collections
- Collection names should be a plural lof the types of documents to be saved.
- Use camelCase if necessary but usually shouldn't have to as the collection name will be one plural word.
- A collection named "" empty string is not valid.
- Collection names should not contain null characters because this defines the end of the collection name.
- Collection names should not start with the prefix "system" as this is reserved for internal collections.
- Don't use the character $ in collection names 

## Fields
- Use camelCase
- Don't use _ as the starting character on any field name. The only field starting with _ should be _id 
- Field names can't contain . dots or null characters and must not start with a $ dollar sign.
