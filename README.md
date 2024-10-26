# PostgreSQL-Store-Procedure-And-Pre-Defined-Functions

## This repository is about how to use store procedure. It is one of the advanced concept concept to make queries easy. Happy Coding!

### What is store prcedure?

#### A stored procedure is a precompiled collection of one or more SQL statements that can be executed as a single unit. They are stored in the database and can be invoked from applications or other SQL statements. Stored procedures are used to encapsulate complex business logic, promote code reuse, and improve performance.

### 1) `Create a users table`

```
CREATE TABLE Users (
    UserID INT PRIMARY KEY,
    Name VARCHAR(100),
    City VARCHAR(100)
);
```

### 2) `Create procedure for addding users`

```
create or replace procedure adduser (username varchar(100), city varchar(100))
language plpgsql
as $$
begin
insert into users (username,city) values (username,city);
end;
$$;
```

### 3) `Call procedure for addding user`

```
call adduser ('muhammad azam', 'islamabad')
```

### `What is User Pre-Defined functions?`

#### A user-defined function (UDF) in PostgreSQL is a function created by users to perform specific operations that are not provided by built-in functions. These functions can encapsulate complex logic, manipulate data, and return results, making them reusable throughout your database.

### Key Features:

- Custom Logic: You can implement business rules or calculations.
- Return Types: UDFs can return various types, including scalar values, rows, or sets.
- Multiple Languages: Functions can be written in various languages like SQL, PL/pgSQL, Python, etc.

### 1) `Create a registerusers table`

```
CREATE TABLE registerusers (
    id SERIAL PRIMARY KEY,
    username VARCHAR(100) NOT NULL,
    country VARCHAR(100)
);

```

### 2) `Insert data into registerusers table`

```
INSERT INTO registerusers (username, country) VALUES
('Uzair', 'In'),
('Farooq', 'Pk'),
('Ahmed', 'Nz');
```

### 3) `Create a function`

```
CREATE OR REPLACE FUNCTION getuserbycountry(country_input VARCHAR(100))
RETURNS TABLE(username VARCHAR(100)) AS $$
BEGIN
    RETURN QUERY
    SELECT ru.username FROM registerusers ru WHERE ru.country = country_input;
END;
$$ LANGUAGE plpgsql;
```

### 4) `Querying data`

```
SELECT * FROM getuserbycountry('In');
```
