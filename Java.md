# Concepts

1. List : 有序，允许重复。有以下3个实现类：
	- LinkedList  
		基于链表实现，链表内存是散列的，效率高，增删快，查询慢;
	- ArrayList  
		基于数组实现，非线程安全，效率高，增删慢，查询快;
	- Vector  
		基于数组实现，线程安全，效率低，增删慢，查询慢;

2. Map : 无序，键值不能重复。
	- HashMap  
		基于Hash表的Map接口实现，非线程安全，高效，支持空值和Null；
	- HashTable  
		线程安全，低效，不支持空值和Null;
	- LinkedHashMap  
		HashMap的一个子类，保存了记录的插入顺序;
	- SortMapTreeMap  
		能够把它保存的记录根据键排序，默认是键值的升序排序;
3. Set : 无序，不允许重复。
	- HashSet  
		底层是由 Hash Map 实现，不允许集合中有重复的值，使用该方式时需要重写 equals()和 hash Code()方法；
	- LinkedHashSet  
		继承于 HashSet，同时又基于 LinkedHashMap 来进行实现，底层使用的是 LinkedHashMap
# Questions

1.	Q:  ArrayList 与 LinkedList的区别

	A:  
		1. ArrayList是基于数组实现的，LinkedList是基于双向链表实现的。
	    2. 对于随机访问，ArrayList优于LinkedList。
		3. 对于插入删除，LinkedList优于ArrayList。
		4. LinkedList比ArrayList更占内存。

2.	Q:	hashmap如何解决hash冲突

	A:	链表法, 在当前hash寻址的地址空间进行链表存储

3.  Q:	为什么hashmap中的链表需要转成红黑树

	A:	

	
		

