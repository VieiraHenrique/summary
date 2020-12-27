# SQL

---

## Connecting php to sql

Connect to a database

```php
// Connect to database
$myConnection = mysqli_connect('host', 'username', 'password', 'name of database');

// Write query for all data in a table
$sql = 'SELECT * FROM tableName';

// Make query
$result = mysqli_query($myConnection, $sql);

// Fetch the resulting rows as an array
$data = mysqli_fetch_all($result, MYSQLI_ASSOC);

// Free results from memory
mysqli_free_results($result);

// Close connection
mysqli_close($myConnection);

print_r($data);

```

## SELECT

```sql
SELECT _what_

FROM _table_

WHERE _condition_

AND/OR _other condition_

LIKE %_entry_%
```

## INSERT

```sql
INSERT INTO _table_ ('column1', 'column2', 'column3') VALUES ('value1', 'value2', 'value3')
```

## UPDATE

```sql
UPDATE _table_ SET _columnName_ = _value_ WHERE _condition_
```

## DELETE

```sql
DELETE FROM _table_ WHERE _condition_
```
