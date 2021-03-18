# MySQL

## 事务

***

MySQL 事务都是指在 InnoDB 引擎下，MyISAM 引擎是不支持事务的。

事务具有原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）四个特性，简称ACID。

- 原子性   
	事务要么完全执行，要么完全不执行

- 一致性  
	事务完成时，数据必须处于一致的状态

- 隔离性  
	同时处理多个事务时，一个事务的执行不能被另一个事务所干扰，事务的内部操作与其他并发事务隔离

- 持久性  
	事务提交后，对数据的修改是永久性的

## 隔离级别

***

SQL标准定义了四种隔离级别，MySQL都支持。四种隔离级别分别是：

- 读未提交（Read Uncommitted）
- 读已提交（Read Committed）
- 可重复读（Repeatable Read）
- 串行化 （Serializable）

从上往下，隔离程度逐渐增强，性能主键变差。采用哪种隔离界别需要根据系统需求均衡决定，其中可重复读是MySql的默认隔离级别。

事务隔离其实是为了解决下面四种问题：

- 脏读（Dirty Read）

	脏读是指当一个事务正在访问数据，并且对数据进行了修改，而这种更改还没有提交到数据库中，这是另外一个事务也访问这个数据，然后使用了这个数据。

- 不可重复读（UnRepeatable Read）

	不可重复读是指事务A多次读同一数据。在事务A没有结束时，另外事务B也访问该数据，那么在事务A的两次读数据之间，由于事务B的修改，同时事务B已经提交，那么事务A两次读到的数据可能是不一样的。

- 幻读（phantom problem）

	幻读是针对数据插入操作来说的，如果事务A对某些行的内容做了更改，但是还没有提交，此时事务B插入了与事务A更改前的记录相同的记录行，并且在事务A提交之前提交了，而这时在事务A查询时，会发现好像刚刚的更改对于某些数据未起作用，但其实是事务B操作的结果，让用户感觉很魔幻，感觉出现了幻觉，这就叫幻读。


	|隔离级别|脏读|不可重复读|幻读|
	|-------|----|---------|----|
	|读未提交|False|False|False|
	|读已提交|True|False|False|
	|可重复读|True|True|False|
	|串行化|True|True|True|



## 索引

***

- Primary Key 主键索引

- Unique 唯一索引

- Fulltext 全文索引

- Key 普通索引

- Spatial 空间索引


### InnoDB Storage Engine Index Characteristics

|Index Class|Index Type|Stores NULL VALUES|Permits Multiple NULL Values|IS NULL Scan Type|IS NOT NULL Scan Type|
|--|--|--|--|--|--|
|Primary key|BTREE|No|No|N/A|N/A|
|Unique|BTREE|Yes|Yes|Index|Index|
|Key|BTREE|Yes|Yes|Index|Index|
|FULLTEXT|N/A|Yes|Yes|Table|Table|
|SPATIAL|N/A|No|No|N/A|N/A|


- 单列索引

- 组合索引
	遵循最左前缀原则



## 锁

***


## 存储引擎

*** 

- InnoDB
	是事务型数据库的首选引擎，支持事务安全表（ACID），其他存储引擎都是非事务安全表。
- 