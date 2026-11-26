# SQL：INSERT / UPDATE / DELETE

```sql
-- 批量插入
INSERT INTO users (name, age) VALUES ('a', 20), ('b', 25);

-- 更新：WHERE 别漏，不加就是全表改
UPDATE users SET age = 21 WHERE name = 'a';

-- 删除：同样先确认 WHERE
DELETE FROM users WHERE id = 1;

-- 改表结构
ALTER TABLE users ADD COLUMN email VARCHAR(100);
```

- UPDATE/DELETE 之前，先拿同样的 WHERE 跑一遍 SELECT，确认影响的行。
- 生产库上改数据，先备份，或者开事务：`BEGIN; ... ; COMMIT;`。
- 批量插入一次写多行，比循环单条快一个数量级。
