# Aggregation Pipeline Stages

List of all aggregation pipeline stages can be found [here](https://docs.mongodb.com/manual/reference/operator/aggregation-pipeline/#aggregation-pipeline-operator-reference)

- `$match` match uses standard MongoDB queries. For each input document it outputs either one document (a match) or zero documents (no match)
- `$group` groups documents by an identifier and applies an accumulator expression. Some of the accumulator expression that can be used by group include
	- `$avg`
	- `$first`
	- `$last`
	- `$max`
	- `$min`
	- `$sum`