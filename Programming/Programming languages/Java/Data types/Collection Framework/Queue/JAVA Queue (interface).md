31-01-2023
10:59
Authors: Tamerlan Khutuev
***
Tags: #programming #java #collections_framework 
***
# Queue
Queue - это очередь.

Наследуется от [[JAVA Collection (interface)]].
Docs: https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html

Реализации:
- [[JAVA LinkedList]]
- [[JAVA PriorityQueue]] - можно управлять приоритетом (сортировкой)
- [[JAVA Deque (interface)]] - двухсторонняя очередь
	- [[JAVA ArrayDeque]]

![](https://blog.skillfactory.ru/wp-content/uploads/2022/06/java-collect-7-6134667.png)

```java
public interface Queue<E> extends Collection<E> {  
	boolean add(E e);  
  
	boolean offer(E e);  
  
	E remove();  
  
	E poll();  
  
	E element();  
  
	E peek();  
}
```