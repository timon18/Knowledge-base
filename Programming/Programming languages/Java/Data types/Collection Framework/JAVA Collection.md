31-01-2023
10:58
Authors: Khutuev Tamerlan
***
Tags: #stub #java #programming 
***
# Collection

Интерфейс описывающий понятия коллекции расширяя [[JAVA Iterable]]. Расширяет понятие коллекции. Он не реализуется напрямую классами, но от него наследуются интерфейсы [[JAVA List]], [[JAVA Set]] и [[JAVA Queue]].
Объекты которые относятся к коллекциям можно перебирать в цикле.

![](https://blog.skillfactory.ru/wp-content/uploads/2022/06/java-collect-1-8144484.png)

-   add(item) — добавляет элемент item в коллекцию;
-   addAll(collection) — добавляет в коллекцию другую коллекцию, ту, что указана в скобках;
-   contains(item) — возвращает true или false в зависимости от того, есть ли в коллекции элемент item;
-   containsAll(collection) — работает так же, как предыдущий, но проверяет наличие в коллекции не элемента, а другой коллекции;
-   remove(item) — удаляет из коллекции указанный элемент;
-   retainAll(collection) — удаляет из коллекции указанную в скобках коллекцию. Обратите внимание: retainAll, не removeAll;
-   clear() — очищает коллекцию, то есть удаляет из нее все элементы;
-   size() — выдает количество элементов в коллекции в формате целого числа;
-   isEmpty() — возвращает true или false в зависимости от того, пуста ли коллекция;
-   toArray() — превращает коллекцию в массив.

```java
public interface Collection<E> extends Iterable<E> {  
	int size();  
  
	boolean isEmpty();  
  
	boolean contains(Object o);  
  
	Iterator<E> iterator();  
  
	Object[] toArray();  
  
	 <T> T[] toArray(T[] a);  
  
	default <T> T[] toArray(IntFunction<T[]> generator) {  
        return toArray(generator.apply(0));  
    }  
  
	boolean add(E e);  
  
	boolean remove(Object o);  
  
	boolean containsAll(Collection<?> c);  
  
	boolean addAll(Collection<? extends E> c);  
  
	boolean removeAll(Collection<?> c);  
  
	default boolean removeIf(Predicate<? super E> filter) {  
        Objects.requireNonNull(filter);  
        boolean removed = false;  
        final Iterator<E> each = iterator();  
        while (each.hasNext()) {  
            if (filter.test(each.next())) {  
                each.remove();  
                removed = true;  
            }  
        }  
        return removed;  
    }  
  
	boolean retainAll(Collection<?> c);  
  
	void clear();  
  
	boolean equals(Object o);  
  
	int hashCode();  
  
	default Spliterator<E> spliterator() {  
        return Spliterators.spliterator(this, 0);  
    }  
  
	default Stream<E> stream() {  
        return StreamSupport.stream(spliterator(), false);  
    }  
  
	default Stream<E> parallelStream() {  
        return StreamSupport.stream(spliterator(), true);  
    }  
}
```