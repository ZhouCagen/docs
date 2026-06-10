<mark>⭐SQL HAVING 子句 </mark>  
在 SQL 中增加 HAVING 子句原因是，WHERE 关键字无法与聚合函数一起使用。

HAVING 子句可以让我们筛选分组后的各组数据。

SQL HAVING 语法
```
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

参数说明:  
column1：要检索的列。  
aggregate_function(column2)：一个聚合函数，例如SUM、COUNT、AVG等，应用于column2的值。  
table_name：要从中检索数据的表。  
GROUP BY column1：根据column1列的值对数据进行分组。  
HAVING condition：一个条件，用于筛选分组的结果。只有满足条件的分组会包含在结果集中。  