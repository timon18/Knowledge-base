31-01-2023
11:00
Authors: Tamerlan Khutuev
***
Tags: #stub #programming #java 
***
# Set
Set - математическое множество в java. Т.е. неупорядоченная коллекция уникальных значений.

Наследуется от [[JAVA Collection (interface)]].

Реализации:
- [[JAVA HashSet]]
- [[JAVA TreeSet]]
- [[JAVA LinkedHashSet]]

![](https://blog.skillfactory.ru/wp-content/uploads/2022/06/java-collect-5-8183945.png)


```java
public interface Set<E> extends Collection<E> {  

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
  
	boolean retainAll(Collection<?> c);  
  
	boolean removeAll(Collection<?> c);  
  
	void clear();  
  
	boolean equals(Object o);  
  
	int hashCode();  
  
    default Spliterator<E> spliterator() {  
        return Spliterators.spliterator(this, Spliterator.DISTINCT);  
    }  
  
    static <E> Set<E> of() {  
        return (Set<E>) ImmutableCollections.EMPTY_SET;  
    }  
  
	static <E> Set<E> of(E e1) {  
        return new ImmutableCollections.Set12<>(e1);  
    }  
  
	static <E> Set<E> of(E e1, E e2) {  
        return new ImmutableCollections.Set12<>(e1, e2);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3, E e4) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3, e4);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3, e4, e5);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3, e4, e5,  
                                               e6);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3, e4, e5,  
                                               e6, e7);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3, e4, e5,  
                                               e6, e7, e8);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3, e4, e5,  
                                               e6, e7, e8, e9);  
    }  
  
	static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10) {  
        return new ImmutableCollections.SetN<>(e1, e2, e3, e4, e5,  
                                               e6, e7, e8, e9, e10);  
    }  
  
    static <E> Set<E> of(E... elements) {  
        switch (elements.length) { // implicit null check of elements  
            case 0:  
                @SuppressWarnings("unchecked")  
                var set = (Set<E>) ImmutableCollections.EMPTY_SET;  
                return set;  
            case 1:  
                return new ImmutableCollections.Set12<>(elements[0]);  
            case 2:  
                return new ImmutableCollections.Set12<>(elements[0], elements[1]);  
            default:  
                return new ImmutableCollections.SetN<>(elements);  
        }  
    }  
  
    static <E> Set<E> copyOf(Collection<? extends E> coll) {  
        if (coll instanceof ImmutableCollections.AbstractImmutableSet) {  
            return (Set<E>)coll;  
        } else {  
            return (Set<E>)Set.of(new HashSet<>(coll).toArray());  
        }  
    }  
}
```