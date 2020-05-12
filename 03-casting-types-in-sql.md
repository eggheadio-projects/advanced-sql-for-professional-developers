# Casting Types in SQL

- when creating columns we need to include their types 

- sometimes we need to coerce a type to another type especially when joining tables 

- to do this we can use `cast` 

```
  postgres=# select cast (now() as date);

  postgres=# slect cast ('100' as integer);
```

- Postgres allows us to use the shorthand `::` between the types in place of using `cast...as...`

```
  postgres=# select now()::date 
``` 

## Example Implementation: 

We have a table where a date column is set as `datetime` type, and we create a new one where a date column is simply the `date` type 

- first create a temporary users table and insert a user... 

```
  postgres=# create temporary table users_temp (create_date date, user_handle uuid, first_name text, last_name text, email text);

  postgres=# insert into users_temp values (now(), uuid_generate_v4(), 'michelle', 'jones');
```

![Casting Types 1 Image](./images/casting-types-1.png)

- then we create an inner join on the `create_date` column... 
```
  postgres=# select create_date from users_temp u inner join (select now() as date) n on u.create_date = n.date; 
```

- this join will not work because one (`n.date`) is using `datetime` and one is using `date`(`create_date`) so we get back an empty join table... 

- we want to cast the `datetime` type as `date`

![Casting Types 2 Image](./images/casting-types-2.png)

```
  postgres=# select create_date from users_temp u inner join (select now()::date as date) n on u.create_date = n.date; 
```
*- `select now()::date as date` is the same as `select cast (now() as date) as date`* 