# Bulk Insert and Export Data with CSV Files

- Using Postgres ... 

- Format: 
```
  postgres=# copy <table name> <column names> from '<full file path to CSV file>' DELIMITER ',' CSV HEADER; 
```
- this comand will bulk insert all rows from the file into the table 

- the `copy` command makes this possible
- defining columns is optional, and renames the columns from the original file. If left out, headers will be pulled in from the imported file. 
- `DELIMITER` defaults to tabs, but with CSV we need to choose commas (this works like a key value pair)
- `CSV` and `HEADER` are two separate options: `CSV` for the file type, `HEADER` tells the `copy` command that the first row in the file contains headers and shouldn't be copied into the DB 

- if you change "from" to "to" you can **export a copy of data** to the file **FROM the DB** as a CSV 
