# 集合框架

## 一、Collection
### 1.1 List (有序可重复)
#### ArrayList:

   Object动态数组结构；线程不安全；随机查询快，增删慢；fail-fast机制；序列化
   
1.扩容机制：

   JDK 1.6和1.7，无参构造器，初始容量为10，加载因子为1，扩容倍数为1.5。
 
   JDK 1.7之后，无参构造器，初始化为0，真正增加时，按1.5倍拷贝扩容。
     
2.添加操作：

   (1）扩容验证
     
   (2）添加元素到尾部或插入指定下标位置
     
3.删除操作：

   下标位置的值移除，之后的数据向前移，将最后的位置为null。
     
4.遍历操作：

   (1）for循环遍历
     
   (2）增强for循环遍历
     
   (3）foreach循环遍历
     
   (4）Iterator迭代器遍历
     
5.解决线程安全：

   (1）Vector(同步互斥Synchronized)
   
   (2）CopyOnWriteArrayList、ConcurrentLinkedQueue
   
   (3）Collections工具类：Collections.synchronizedList 
   
#### Vector:

   与ArrayList结构类似，加Synchronized关键字，线程安全；Stack继承自Vector；
   默认初始容量为10，加载因子为1，扩容倍数为2。

#### LinkList:

   双向链表结构；线程不安全；随机查询慢，增删快。
   
   遍历原理：索引值靠近表头近，从节点头部遍历；索引值大于链表一半，从节点尾部遍历。

### 1.2 Set (无序不可重复)

#### SortedSet:

#### HashSet:

#### EnumSet:

### 1.3 Queue（先进先出FIFO）

#### PriorityQueue:

#### Deque:

## 二、Map