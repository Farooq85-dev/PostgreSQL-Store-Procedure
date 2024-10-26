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
