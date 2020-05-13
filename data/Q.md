# ACID
+ **Atomicity**: Store data in all or nothing approach. Full Transaction happens or rollbacks incomplete transaction.
+ **Consistency**: Gives consistent picture of data i.e after making the change, next fetch should reflect that change.
+ **Isolation**: Prevent concurrent data updates from incorrect reads/writes.
+ **Durability**: After COMMIT , makes sure data is safe until destroyed explicitly.

# PostgreSql Terms vs Industry Relational DB Terms
+ Table = Relation
+ Row = Tuple
+ Column = Attribute
