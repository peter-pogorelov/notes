## Some code snippets from Cassandra: Definitive Guide

The following queries can be executed either from cqlsh or from DBeaver. The simplest option is to use DBeaver.

### Create keyspace
```
CREATE KEYSPACE my_keyspace WITH replication = {
    'class': 'SimpleStrategy',
    'replication_factor': 2
}
```

### Create table
```
CREATE TABLE my_keyspace.users (
    first_name text,
    last_name text,
    PRIMARY KEY (first_name)
);
```

### Populate table
```
INSERT INTO my_keyspace.users (first_name, last_name) VALUES ('vasya', 'pupkin');
INSERT INTO my_keyspace.users (first_name, last_name) VALUES ('kolya', 'ivanov');
INSERT INTO my_keyspace.users (first_name, last_name) VALUES ('anatoliy', 'petrov');
```

### Fetch all rows
```
SELECT * FROM my_keyspace.users
```

### Fetch number of rows
```
SELECT COUNT(*) FROM my_keyspace.users
```

### Delete column last_name for user with first_name = 'vasya' and check results
```
DELETE last_name FROM my_keyspace.users WHERE first_name = 'vasya';
SELECT * FROM my_keyspace.users;
```