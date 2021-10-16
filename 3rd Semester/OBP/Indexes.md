tags: [[algebra]] [[OBP Index]] 
## [[Indexes]]
Indexes help minimize search times by indexing data on disk.
###### _Syntax:_
```sql
create clustered | nonclustered index I_name on Table(Column) [include (column, ...)]
drop index I_name on Table
```

`clustered`: can only exist once per table, it is the primary key index
`nonclustered`: multiple per table can exist

Creating an index reduces the number of pages needing to be looked up.
[[IO statistics]]
