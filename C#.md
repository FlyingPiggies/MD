# C#

C#是一门语言，用于生成面向.net平台的代码。


# IEnumerable VS IQueryable

所有对于IEnmurable的过滤，排序等操作，都是在内存中发生的，已经从数据库取出到内存。
所有对于IQueryable的过滤，排序等操作，只有在数据真正用到的时候，才会到数据库中插叙

IQueryable继承了IEnumerable接口，有三个特殊的属性：Type ElementType，Expression Expression（表达式树）， IQueryableProvider Provider（查询提供程序）

IQueryable接口会把查询表达式先缓存到表达式树中，只有真正遍历发生的时候，才会由IQueryProvider解析表达式树，生成sql语句执行数据库查询操作


# IEnumerable VS IEnumerator

继承IEnumerable的类需实现GetEnmuerator方法，返回一个IEnumerator接口对象。
可以说，IEnumerable和IEnumerator工作的方式是一样的。

但由于IEnumerable内部实现了IEnumerator，所以使用IEnumerable遍历一个List时候，可以写更少的代码。

但是IEnumerator可以保存遍历对象的状态。

#

属性（get set）


voliatle