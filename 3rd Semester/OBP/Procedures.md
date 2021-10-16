tags: [[algebra]] [[OBP Index]] 
## [[Procedures]]
###### _Syntax_
```sql
create | alter proc[edure] name
	[@variable type [output]]+
as
	commands
	
exec[ute] name ([variable]+ | [@innervariable = outervariable]+) 

drop proc[edure] name
```

Procedures are SQL's answer to reusable functions, they are stored server side, just like views, tables and the like.

`create | alter proc[edure]`: call for creating a procedure
- `[@variable type]+`: one or more variables
	- `[output]`: defines a variable as an output, to be returned from the procedure
- `as`: commands to be preformed follow after the `as` keyword


`exec | execute`: subquerrys are disallowed
-	`name`: name of procedure
-	`[variable]+` : one or more variables, in order _(subquerrys are disallowed)_
-	`[@innervariable = outervariable]+`: one or more variables, explicitely declared
