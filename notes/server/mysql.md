# mysql

## 常用命令
```
mysql -h mysql.sqlpub.com -u username -p
Enter password:

mysql>
SHOW DATABASES;
USE database_name;

SHOW TABLES;
DESCRIBE table_name; 
SELECT * FROM table_name;
```



MySQL 命令：

1. **启动 MySQL 服务**：

   ```
   sudo systemctl start mysql
   ```

2. **停止 MySQL 服务**：

   ```
   sudo systemctl stop mysql
   ```

3. **重启 MySQL 服务**：

   ```
   sudo systemctl restart mysql
   ```

4. **查看 MySQL 服务状态**：

   ```
   sudo systemctl status mysql
   ```

5. **登录 MySQL**：

   ```
   mysql -u username -p
   ```

   输入用户名和密码后登录 MySQL 服务器。

6. **查看所有数据库**：

   ```
   SHOW DATABASES;
   ```

7. **创建数据库**：

   ```
   CREATE DATABASE database_name;
   ```

8. **删除数据库**：

   ```
   DROP DATABASE database_name;
   ```

9. **选择数据库**：

   ```
   USE database_name;
   ```

10. **查看数据库中的所有表**：

    ```
    SHOW TABLES;
    ```

11. **创建数据表**：

    ```
    CREATE TABLE table_name (
      column1 datatype,
      column2 datatype,
      ...
    );
    ```

12. **删除数据表**：

    ```
    DROP TABLE table_name;
    ```

13. **查看表结构**：

    ```
    DESCRIBE table_name;
    ```

14. **插入数据**：

    ```
    INSERT INTO table_name (column1, column2) VALUES (value1, value2);
    ```

15. **查询数据**：

    ```
    SELECT * FROM table_name;
    ```

16. **更新数据**：

    ```
    UPDATE table_name SET column1 = value1 WHERE condition;
    ```

17. **删除数据**：

    ```
    DELETE FROM table_name WHERE condition;
    ```

18. **添加新列**：

    ```
    ALTER TABLE table_name ADD COLUMN new_column datatype;
    ```

19. **修改列名**：

    ```
    ALTER TABLE table_name CHANGE old_column_name new_column_name datatype;
    ```

20. **删除列**：

    ```
    ALTER TABLE table_name DROP COLUMN column_name;
    ```

21. **设置外键约束**：

    ```
    ALTER TABLE table_name ADD CONSTRAINT constraint_name FOREIGN KEY (column_name) REFERENCES other_table_name(other_column_name);
    ```

22. **删除外键约束**：

    ```
    ALTER TABLE table_name DROP FOREIGN KEY constraint_name;
    ```

23. **导出数据库**：

    ```
    mysqldump -u username -p database_name > dump_file.sql
    ```

24. **导入数据库**：

    ```
    mysql -u username -p database_name < dump_file.sql
    ```

25. **查看当前时间**：

    ```
    SELECT NOW();
    ```

26. **计算数据库中的行数**：

    ```
    SELECT COUNT(*) FROM table_name;
    ```

27. **限制查询结果**：

    ```
    SELECT * FROM table_name LIMIT 10;
    ```

28. **排序查询结果**：

    ```
    SELECT * FROM table_name ORDER BY column_name ASC;
    ```

29. **分组查询**：

    ```
    SELECT column_name, COUNT(*) FROM table_name GROUP BY column_name;
    ```

30. **连接查询**：

    ```
    SELECT * FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;
    ```

这些命令覆盖了 MySQL 的基本操作，包括数据库和数据表的创建、数据的增删改查等。