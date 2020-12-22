# BSON Objects
#mongodb 

BSON stands for Binary-encoded JSON.

JSON documents in MongoDB are stored in a binary representation called BSON. Unlike other databases that store JSON data as simple strings and numbers, the BSON encoding extends the JSON representation to include additional types such as int, long, date, floating point and decimal 128. 

There are two families of types for representing BSON data:

## D Types
The D family of types is used to build BSON objects using native Go types. This can be useful for constructing commands passed to MongoDB. The D family consists of four types:

- D: A BSON document. This type should be used in situations where order matters such as MongoDB commands.
- M: An unordered map. It is the same as D except it does not preserve order.
- A: A BSON array.
- E: A single element inside a D.

Here is an example of a filter document built using D types which may be used to find documents where the `name` field matches either `Alice` or `Bob`

bson.D{{
	"name",
	bson.D{{
			"$in",
			bson.A{"Alice", "Bob"}
	}}
}}
