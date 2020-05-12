## Import Data

### Create Users
```sql
copy users(user_handle,first_name,last_name,email,gender,age,language) FROM '/Users/zac/Documents/01. Projects/advanced-sql-pt/user-data.csv' DELIMITER ',' CSV HEADER;
```

### Create Purchases
```sql
copy purchases(date,user_handle,sku,quantity) FROM '/Users/zac/Documents/01. Projects/advanced-sql-pt/purchases-data.csv' DELIMITER ',' CSV HEADER;
```

### Create Products
```sql
copy products(sku,product,price) FROM '/Users/zac/Documents/01. Projects/advanced-sql-pt/product-data.csv' DELIMITER ',' CSV HEADER;
```
