# Create a Custom Enum Type 

**- data integrity is something you should always have in mind**

- we can ensure integrity by adding constraints to our tables  

- a powerful feature of SQL is the ability to create our own types 

```
  create type user_status as enum ('member', 'instructor', 'developer');
  CREATE TYPE
```

- We create a data type called `user_status` as an `enum` and give it the string options of `member`, `instructor`, `developer` 

- we can then add a column on our users table using this newly create type...
```
  postgres=# alter table users add column status user_status 
```

- Now we can update a users status using our custom user_status type... 
```
  postgres =# update users set status = 'instructor' where first_name = 'Lucie'; 
```

__- using a custom enum will save us from misspellings and data errors since it *requires* that we use one of the strings we previously defined__