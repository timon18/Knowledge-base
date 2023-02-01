31-01-2023
12:24
Authors: Tamerlan Khutuev
***
Tags: #programming #java #collections_framework 
***
# HashSet
HashSet - это неупорядоченная коллекция уникальных значений. У него даже нет методов get и тому подобных. Для поиска можно просто пройтись в цикле. 

Использует HashMap [[JAVA HashMap]] для хранения данных. Так как HashMap использует ключ значение, а HashSet нет, то как ключ просто записывается объект который мы сохраняем, а в качестве значения просто пустой объект (константа PRESENT). 

Код из библиотеки:
```java
public class HashSet<E>  extends AbstractSet<E> implements Set<E>, Cloneable, java.io.Serializable  
{
	// Dummy value to associate with an Object in the backing Map  
	private static final Object PRESENT = new Object();

	public HashSet() {  
	    map = new HashMap<>();  
	}
	//...

	public boolean add(E e) {  
	    return map.put(e, PRESENT)==null;  
	}
}
```

Реализует интерфейс Map [[JAVA Set (interface)]].
Docs: https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html