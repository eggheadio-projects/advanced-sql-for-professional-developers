# [Casting Types in SQL](https://egghead.io/lessons/postgresql-casting-types-in-sql)

When creating columns we need to include their types.

Sometimes we need to coerce a type to another type especially when joining tables, to do this we can use `cast`:

```postgres
  postgres=# select cast (now() as date);

  postgres=# slect cast ('100' as integer);
```

Postgres allows us to use the shorthand `::` between the types in place of using `cast...as...`:

```postgres
  postgres=# select now()::date 
``` 

## Example Implementation: 

We have a table where a date column is set as `datetime` type, and we create a new one where a date column is simply the `date` type. 

The first create a temporary users table and insert a user:

```postgres
  postgres=# create temporary table users_temp (create_date date, user_handle uuid, first_name text, last_name text, email text);

  postgres=# insert into users_temp values (now(), uuid_generate_v4(), 'michelle', 'jones');
```

Then we create an inner join on the `create_date` column:

```postgres
  postgres=# select create_date from users_temp u inner join (select now() as date) n on u.create_date = n.date; 
```

This join will not work because one (`n.date`) is using `datetime` and one is using `date`(`create_date`) so we get back an empty join table: 

We want to cast the `datetime` type as `date`:

```postgres
  postgres=# select create_date from users_temp u inner join (select now()::date as date) n on u.create_date = n.date; 
```

Noe, `select now()::date as date` is the same as `select cast (now() as date) as date`.