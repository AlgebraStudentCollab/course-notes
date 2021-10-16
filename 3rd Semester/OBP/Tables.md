tags: [[algebra]] [[OBP Index]] 
## [[Tables]]
A table stores data arranged in strictly defined columns and rows
###### _Syntax:_
```sql
CREATE TABLE Name (
	column_name data_type [CONSTRAINT],
	column_name data_type [CONSTRAINT],
	...
)
```

`[NOT NULL]`: Ensures that a column cannot have a NULL value
`[UNIQUE]`: Ensures that all values in a column are different
`[PRIMARY KEY]`: A combination of a `NOT NULL` and `UNIQUE`. Uniquely identifies each row in a table
`IDENTITY(N, M)`: Automatically increments the column starting from `N`, increasing by `M`
`[FOREIGN KEY]`: Prevents actions that would destroy links between tables
`[CHECK]`: Ensures that the values in a column satisfies a specific condition
`[DEFAULT]`: Sets a default value for a column if no value is specified
`[CREATE INDEX]`: Used to create and retrieve data from the database very quickly