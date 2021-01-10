## EP 3

[[Microservices by Nic Jackson]]

RESTful services. REST stands for representational state transfer. gRPC is a totally different ball park. When people say RESTful they usually mean JSON over HTTP. 

Creating a product API. Create a type for the data model. Start by keeping things in memory, like a statically defined product list.

`
type Product struct {
	ID			int
	Name		string
	Description string
	Price		float32
	SKU			string
	CreatedOn	string
	UpdatedOn 	string
	DeletedOn	string
}

var productList = []*Product{
	&Product{
		ID: 1,
		Name: "Latte",
		Description "Frothy milky coffee",
		Price: 2.45,
		SKU: "abc323",
		CreatedOn: time.Now().UTC.String(),
		updatedOn: time.Now().UTC.String(),
	},
	&Product{
		ID: 2,
		Name: "Espresso",
		Description: "short and strong coffee without milk",
		Price: 1.99,
		SKU: "fjd34",
		CreatedOn: time.Now().UTC.String(),
		updatedOn: time.Now().UTC.String(),
	}
}
`

In a real world multi-tier application it much easier to explain the layers involved in a microservices application.
- product api
- presentation layers
- backend services

## Product API
- Needs the ability to return some coffee
- This API will be consumed by the frontend and the mobile app.

encoding/json in standard library allows marshalling between struct and json.

Abstract the logic of where the data is coming from, from the rest of the code.


