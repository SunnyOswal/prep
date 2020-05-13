# ACID
+ **Atomicity**: Store data in all or nothing approach. Full Transaction happens or rollbacks incomplete transaction.
+ **Consistency**: Gives consistent picture of data i.e after making the change, next fetch should reflect that change.
+ **Isolation**: Prevent concurrent data updates from incorrect reads/writes.
+ **Durability**: After COMMIT , makes sure data is safe until destroyed explicitly.

# Different Type of NoSql DataStores ?
+ **Document Store**: Data in JSON documents. 
    + MongoDB
+ **Key-Value Store**: Data in key-value pair.
    + Redis
+ **Wide Column Store**: store data in tables, rows, and dynamic columns. Wide-column stores provide a lot of flexibility over relational databases because each row is not required to have the same columns.
    + Cassandra
+ **Graph** : store data in nodes and edges.
    + Gremlin
# PostgreSql Terms vs Industry Relational DB Terms
+ Table = Relation
+ Row = Tuple
+ Column = Attribute

# How to check Query Plan for queries ?
+ PostgreSQL (below commands)
  + EXPLAIN : displays estimated costs.
  + EXPLAIN ANALYZE : will execute the query. This command displays both estimated and actual costs.
  + EXPLAIN ANALYZE SELECT * FROM pg_indexes: Analyzing indexes.
