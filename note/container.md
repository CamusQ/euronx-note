# 容器
* [JDK容器链接](https://docs.oracle.com/javase/10/docs/api/java/util/doc-files/coll-overview.html)
* 在Collection<T>中也可以加入T的子类型
容器分为两大部分：collection保存单一元素和map保存键值对，也可以加上数组
向上转型也可以像作用于其他类型一样作用于泛型
容器在创建的时候大都以接口的形式创建引用
再利用Arrays.asList()创建list时如果将其放入构造器则产生一份副本
如果直接将其当做list使用，则本质上还是在操作数组（不能增删，toString）
Iterator 接 口（看着像对象）可以遍历并选择序列中的对象
经常通过匿名内部类实现，所以基本上看不到实例类名
Iterator的的好处是可以将遍历的操作与底层实现分离
Iterable 接 口 表示这个类是可迭代的（Iterable）
也表示的容器之间的共通性（所有的Collection都实现了Iterable）
Collection是描述所有序列容器之间的共性的根接口（都可以提供Iterator）
AbstractCollection是他的默认实现
自定义一个集合类的时候，实现Collection接口会非常复杂，因为要实现许多方法
所以可以继承absCollection类，只需要重写iterator（）方法
一个类可以继承Iterable接口，利用里面的iterator()方法产生的匿名Iterator对象来iterate类中的元素
foreach需要的是Collection（Iterable），while()结构需要的是Iterator
数组可以用于foreach，但是数组不是Iterable
Iterator单独出现好像没什么意义
适配器方法可以用于多种方法遍历，通过产生多种不同的Iterable匿名内部类
Map
加入：put：此方法返回上一个与参数key相关联的value，如果此value不存在于map中返回null
获取key：get：参数是一个Object，与collection中的get参数类似，因为泛型的擦除所导致
获取value：value存在多个，无法获取
查找key：containsKey
查找value：containsValue
获取全部key：ketSet，返回一个set，因为key无法重复
获取全部value：values返回一个collection，value可以重复
Entry是一个键值对，相对于获取key和value，entry一次可以获得俩
entrySet是存储Entry的set
自定义map的时候，要实现entrySet方法，使得map可以遍历自己的entry
而自定义一个Entry的时候，必须实现两种判断对象是否相等的方法（未知），和获取Entry中K，V，设置V的方法
Entry<K,V> == Pair<K,V>
作为map的键的对象必须实现hashcode和equals
subList方法返回的只是一个list的视图，不能当做list使用，且是前包含，后不包含
Arrays.asList（）返回值是一个LIst，但是使用的时候是一个ArrayList，可能机制就是这样子吧
且此方法的T，为参数列表中最大的对象的类型
Collections.reverseOrder()返回一个跟自然排序相反的comparator
Collections.nCopys和fill方法都是用一个对象的引用填充容器
队列
 	Throws exception 	Returns special value
Insert 	add(e) 			offer(e)
Remove 	remove() 		poll()
Examine element() 		peek()
sortedMap(Set)是TreeMap(Set)的实现
hashCode为了快速存取，equels为了判断是否相等
在HashSet（map）中，先用还是从的找的对象的slot，然后用equels方法判断是否相等
默认的hashCode用对象地址计算，默认的equels用对象地址判断
散列先划定一个范围，equels具体负责判断
copy和nCopys（）
copy将一个容器中的元素全部覆盖进另一个容器
nCopys返回一个由n个T对象构成的List
数组和容器在使用带有comparator的sort时，如果使用binarySearch时，必须使用相同的comparator
Collections.unmodifiedCollection()利用参数里的容器，返回一个只读的容器
对于只读容器的修改，不会引起编译器错误，但是会引起异常
