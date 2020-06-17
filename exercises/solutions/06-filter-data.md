## 01
```sql
SELECT 
  u.user_handle, 
  sum(p.quantity) 
FROM 
  users u 
LEFT JOIN
  purchases p 
ON 
  u.user_handle = p.user_handle 
WHERE 
  u.age > 19 
AND 
  u.age < 30 
AND 
  u.gender = 'Female' 
GROUP BY 
  u.user_handle 
HAVING 
  sum(p.quantity) > 100 
ORDER BY 
  user_handle;
```
Answer:
```
user_handle | sum 
-------------+-----
           2 | 146
          36 | 126
          93 | 110
```

## 02
```sql
postgres=# select email, users.user_handle, age, gender, sum(quantity) as total from users join purchases on (users.user_handle = purchases.user_handle) where sku=18302880 group by users.user_handle;
       email          | user_handle | age | gender | total
------------------------<del>-------------</del>-----<del>--------</del>--&#x2013;&#x2014;
atanslief@berkeley.edu | 16 | 19 | Male | 12
(1 row)
```