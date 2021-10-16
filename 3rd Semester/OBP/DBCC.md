tags: [[algebra]] [[OBP Index]] 
## [[DBCC]] ( #Transact-SQL )
**D**ata**b**ase **c**onsole **c**ommands
###### _Syntax:_
```sql
dbcc traceon(3604)
dbcc ind('DatabaseName', 'TableName', IndexID)
dbcc page('DatabaseName', FileNumber, PageNumber, VerboseLevel) [with tableresults]
```

`dbcc traceon(3604)`: creates dbcc session to last untill we log out
`dbcc ind`: searches through table index, revealing page numbers and types
- `DatabaseName`: name or object id of database
- `'TableName'`: name or object id of table in said database
- `'IndexID'`: id of index to list, -1 lists all indices
