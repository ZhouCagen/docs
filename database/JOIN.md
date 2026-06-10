<mark>⭐SQL JOIN</mark> 

SQL JOIN 子句用于把来自两个或多个表的行结合起来，基于这些表之间的共同字段。

最常见的 JOIN 类型：SQL INNER JOIN（简单的 JOIN）。 SQL INNER JOIN 从多个表中返回满足 JOIN 条件的所有行。

语法：
```
SELECT column1, column2, ...
FROM table1
JOIN table2 ON condition;
```
参数说明：  
column1, column2, ...：要选择的字段名称，可以为多个字段。如果不指定字段名称，则会选择所有字段。  
table1：要连接的第一个表。  
table2：要连接的第二个表。  
condition：连接条件，用于指定连接方式。  
