31-01-2023
11:00
Authors: Tamerlan Khutuev
***
Tags: #programming #java 
***
# List
List - упорядоченная коллекция данных. У элементов есть индексы который показывают их положение в списке. 

Наследуется от [[JAVA Collection (interface)]].

Реализации:
- [[JAVA ArrayList]] - реализация динамического массива объектов
- [[JAVA LinkedList]] - двунаправленный связный список
- [[JAVA Vector]] - реализация динамического массива объектов (потокобезопасный)
	- [[JAVA Stack]] - стек (частично потокобезопасный)

![](https://blog.skillfactory.ru/wp-content/uploads/2022/06/java-collect-4-6637877.png)

```java
public interface List<E> extends Collection<E> {  
	int size();  
  
	boolean isEmpty();  
  
	boolean contains(Object o);  
  
	Iterator<E> iterator();  
  
	Object[] toArray();  
  
	<T> T[] toArray(T[] a);  
  
	boolean add(E e);  
  
	boolean remove(Object o);  
  
  
	boolean containsAll(Collection<?> c);  
  
	boolean addAll(Collection<? extends E> c);  
  
	boolean addAll(int index, Collection<? extends E> c);  
  
	boolean removeAll(Collection<?> c);  
  
	boolean retainAll(Collection<?> c);  
  
	default void replaceAll(UnaryOperator<E> operator) {  
        Objects.requireNonNull(operator);  
        final ListIterator<E> li = this.listIterator();  
        while (li.hasNext()) {  
            li.set(operator.apply(li.next()));  
        }  
    }  
  
    default void sort(Comparator<? super E> c) {  
        Object[] a = this.toArray();  
        Arrays.sort(a, (Comparator) c);  
        ListIterator<E> i = this.listIterator();  
        for (Object e : a) {  
            i.next();  
            i.set((E) e);  
        }  
    }  
  
	void clear();  
  
	boolean equals(Object o);  
  
	int hashCode();  
  
	E get(int index);  
  
	E set(int index, E element);  
  
	void add(int index, E element);  
  
	E remove(int index);  
  
	int indexOf(Object o);  
	
	int lastIndexOf(Object o);  
  
	ListIterator<E> listIterator();  
  
	ListIterator<E> listIterator(int index);  
  
	List<E> subList(int fromIndex, int toIndex);  
  
    default Spliterator<E> spliterator() {  
        if (this instanceof RandomAccess) {  
            return new AbstractList.RandomAccessSpliterator<>(this);  
        } else {  
            return Spliterators.spliterator(this, Spliterator.ORDERED);  
        }  
    }  
  
    static <E> List<E> of() {  
        return (List<E>) ImmutableCollections.EMPTY_LIST;  
    }  
  
	static <E> List<E> of(E e1) {  
        return new ImmutableCollections.List12<>(e1);  
    }  
  
	static <E> List<E> of(E e1, E e2) {  
        return new ImmutableCollections.List12<>(e1, e2);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3, E e4) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3, e4);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3, E e4, E e5) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3, e4, e5);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3, e4, e5,  
                                                         e6);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3, e4, e5,  
                                                         e6, e7);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3, e4, e5,  
                                                         e6, e7, e8);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3, e4, e5,  
                                                         e6, e7, e8, e9);  
    }  
  
	static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10) {  
        return ImmutableCollections.listFromTrustedArray(e1, e2, e3, e4, e5,  
                                                         e6, e7, e8, e9, e10);  
    }  
	
    static <E> List<E> of(E... elements) {  
        switch (elements.length) { // implicit null check of elements  
            case 0:  
                @SuppressWarnings("unchecked")  
                var list = (List<E>) ImmutableCollections.EMPTY_LIST;  
                return list;  
            case 1:  
                return new ImmutableCollections.List12<>(elements[0]);  
            case 2:  
                return new ImmutableCollections.List12<>(elements[0], elements[1]);  
            default:  
                return ImmutableCollections.listFromArray(elements);  
        }  
    }  
  
	static <E> List<E> copyOf(Collection<? extends E> coll) {  
        return ImmutableCollections.listCopy(coll);  
    }  
}
```