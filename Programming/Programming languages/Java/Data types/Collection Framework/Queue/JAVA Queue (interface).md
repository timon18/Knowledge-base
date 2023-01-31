31-01-2023
10:59
Authors: Tamerlan Khutuev
***
Tags: #stub #programming #java 
***
# Queue
Queue - это очередь.

Наследуется от [[JAVA Collection (interface)]].

Реализации:
- [[JAVA LinkedList]]
- [[JAVA ArrayDeque]]
- [[JAVA PriorityQueue]]

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