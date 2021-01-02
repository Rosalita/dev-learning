# Aggregation Pipeline

MongoDBs aggreggation framework is modeled on the concept of data processing pipelines. Documents enter a multi-stage pipeline that transforms the documents into an aggregated result.

An example of an aggregation pipeline is 

`db.orders.aggregate([
   { $match: { status: "A" } },
   { $group: { _id: "$cust_id", total: { $sum: "$amount" } } }
])`

This pipeline has two stages `$match` and `$group`

The match stage filters the results.
The group stage groups the documents by customer ID and calculates the sum of each customers amount.

There are many different [[Aggregation Pipeline Stages]]