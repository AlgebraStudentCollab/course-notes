tags: [[algebra]] [[OBP Index]] 
## [[Variables]]
### Declaration
```sql
declare @name type
```

Variables must be declared before they are used. And can use any of the SQL Data Types[^type]

### Setting
```sql
set @name = data

set @name (
	select ...
)

select @name = column from table

select @name
```

Variables can only hold one value, with 3 different ways of setting them.
1.	`set @name = data` : explicitly
2.	`set @name ( select ... )`: nested select, must return 1 value
3.	`select @name = column from table`: becomes the value of column in the last row sorted by the primary key

[^type]: #SQLDataTypes 