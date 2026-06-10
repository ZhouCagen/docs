✅ OBJECT_ID 的语法  
```
OBJECT_ID ( 'database_name.schema_name.object_name' , 'object_type' )
```

或最常用的简写：
```
OBJECT_ID ('object_name' , 'object_type')
```

🔹 常用 object_type
```
'U'   -- 用户表
'V'   -- 视图
'P'   -- 存储过程
'TR'  -- 触发器
'FN'  -- 标量函数
'IF'  -- 内联表值函数
'TF'  -- 多语句表值函数
```

🔹 判断对象是否存在的标准写法  
```
IF OBJECT_ID('对象名', '对象类型') IS NOT NULL
    DROP 对象;
```