tags: [[algebra]] [[OBP Index]] 
## [[Views]]
A view is like a select stored into a table as a pointer. No data is stored in a view.
It behaves like any other table, it can insert and delete columns, if c
###### _Syntax:_
```sql
create view vw_Name
[with [encryption], [schemabinding]]
as
select ...
[with check option]
```

`with encryption`: encrypts data about the table
`with schemabinding`: disallows making changes to the underlying tables
`with check option`: disallows inserting data that would not be visible in the table
