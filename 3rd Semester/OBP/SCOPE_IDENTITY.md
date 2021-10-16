tags: [[algebra]] [[OBP Index]] 
## [[SCOPE_IDENTITY|SCOPE_IDENTITY()]]
```sql
declare @id = SCOPE_IDENTITY()

insert into Table (Name, ID) 
values ('Agra', @ID), ('Delhi', @ID)
```

`SCOPE_IDENTITY()`: Evaluates to the last used ID in the current scope.

#SQLfunction