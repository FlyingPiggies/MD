# Sql优化

## 对于MySQL层优化我一般遵从五个原则：

- 减少数据访问： 设置合理的字段类型，启用压缩，通过索引访问等减少磁盘IO
- 返回更少的数据： 只返回需要的字段和数据分页处理 减少磁盘io及网络io
- 减少交互次数： 批量DML操作，函数存储等减少数据连接次数
- 减少服务器CPU开销： 尽量减少数据库排序操作以及全表查询，减少cpu 内存占用
- 利用更多资源： 使用表分区，可以增加并行操作，更大限度利用cpu资源

总结到SQL优化中，就三点:

1. 最大化利用索引；
2. 尽可能避免全表扫描；
3. 减少无效数据的查询；

一、避免不走索引的场景
1. 尽量避免在字段开头模糊查询，会导致数据库引擎放弃索引进行全表扫描。如下：

    `SELECT * FROM t WHERE username LIKE '%陈%'`

    优化方式：尽量在字段后面使用模糊查询。如下：

    `SELECT * FROM t WHERE username LIKE '陈%'`

2. 尽量避免使用in 和not in，会导致引擎走全表扫描。如下：

    `SELECT * FROM t WHERE id IN (2,3)`

    优化方式：
    
    如果是连续数值，可以用between代替。如下：

    如果是子查询，可以用exists代替。

    -- 不走索引

    `select * from A where A.id in (select id from B);`

    -- 走索引

    `select * from A where exists (select * from B where B.id = A.id);`

3. 尽量避免使用 or，会导致数据库引擎放弃索引进行全表扫描。如下：

    `SELECT * FROM t WHEREid = 1 OR id = 3`
    
    优化方式：可以用union代替or。如下

    ```
    SELECT * FROM t WHERE id = 1
    UNION
    SELECT * FROM t WHERE id = 3
    ```

4. 尽量避免进行null值的判断，会导致数据库引擎放弃索引进行全表扫描。如下：

    `SELECT * FROM t WHERE score IS NULL`
    
    优化方式：可以给字段添加默认值0，对0值进行判断。如下：

    `SELECT * FROM t WHERE score = 0`

5. 尽量避免在where条件中等号的左侧进行表达式、函数操作，会导致数据库引擎放弃索引进行全表扫描。可以将表达式、函数操作移动到等号右侧。如下：
    
    -- 全表扫描

    `SELECT * FROM T WHERE score/10 = 9;`

    -- 走索引

    `SELECT * FROM T WHERE score = 10*9;`

6. 当数据量大时，避免使用where 1=1的条件。通常为了方便拼装查询条件，我们会默认使用该条件，数据库引擎会放弃索引进行全表扫描。如下：

    `SELECT username, age, sex FROM T WHERE 1=1`

    优化方式：用代码拼装sql时进行判断，没 where 条件就去掉 where，有where条件就加 and。

7. 查询条件不能用 <> 或者 !=

    使用索引列作为条件进行查询时，需要避免使用<>或者!=等判断条件。如确实业务需要，使用到不等于符号，需要在重新评估索引建立，避免在此字段上建立索引，改由查询条件中其他索引字段代替。

8. where条件仅包含复合索引非前置列 如下：复合（联合）索引包含key_part1，key_part2，key_part3三列，但SQL语句没有包含索引前置列"key_part1"，按照MySQL联合索引的最左匹配原则，不会走联合索引。

    `select col1 from table where key_part2=1 and key_part3=2`

9. 隐式类型转换造成不使用索引 如下SQL语句由于索引对列类型为varchar，但给定的值为数值，涉及隐式类型转换，造成不能正确走索引。

    `select col1 from table where col_varchar=123; `

10. order by 条件要与where中条件一致，否则order by不会利用索引进行排序

    -- 不走age索引
    `SELECT * FROM t order by age;`

    -- 走age索引
    `SELECT * FROM t where age > 0 order by age;`


> https://zhuanlan.zhihu.com/p/265852739