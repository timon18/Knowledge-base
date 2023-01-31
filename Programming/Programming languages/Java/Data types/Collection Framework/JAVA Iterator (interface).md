31-01-2023
11:22
Authors: Tamerlan Khutuev
***
Tags: #stub #java #programming #collections_framework 
***
# Iterator

Методы итератора — это next(), который возвращает следующий элемент, remove(), который удаляет текущий элемент, и hasNext() — он показывает, существует ли в коллекции следующий элемент.

```java
public interface Iterator<E> {  
	boolean hasNext();  

	E next();  
	
	default void remove() {  
        throw new UnsupportedOperationException("remove");  
    }  
  
	default void forEachRemaining(Consumer<? super E> action) {  
        Objects.requireNonNull(action);  
        while (hasNext())  
            action.accept(next());  
    }  
}
```