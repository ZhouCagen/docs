<mark>⭐GROUP BY 语句 </mark>

GROUP BY 语句用于结合聚合函数，根据一个或多个列对结果集进行分组。  
SQL GROUP BY 语法  

```
SELECT column_name, aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
```