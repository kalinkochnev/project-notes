# Table creation
```sql
CREATE TABLE IF NOT EXISTS <table name> (
	field1 <datatype>
	...
)
```
- SQLite contains schema table `sqlite_schema` which contains info about other tables in db
https://www.sqlite.org/schematab.html


# Types
- Enforce not null with `fieldname <type> NOT NULL`
```sql
INTEGER
VARCHAR(<N CHARS>)
```

https://sqlite.org/datatype3.html

# Foreign keys
https://www.sqlite.org/foreignkeys.html
# Create one to many relationship
https://stackoverflow.com/a/13262880

