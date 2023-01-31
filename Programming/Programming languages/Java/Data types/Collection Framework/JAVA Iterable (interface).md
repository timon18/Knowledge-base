31-01-2023
11:14
Authors: Tamerlan Khutuev
***
Tags: #stub #java #programming 
***
# Iterable

Это основной корневой интерфейс [[JAVA Collections Framework]]. Он означает, что объект итерируемый. У Iterable и, соответственно, у всех интерфейсов, которые от него наследуются, есть метод iterator(). Он возвращает итератор [[JAVA Iterator (interface)]] — специальную сущность-«перечислитель», своеобразный курсор, который указывает на тот или иной объект.

```java
public interface Iterable<T> {   
    Iterator<T> iterator();  
  
    default void forEach(Consumer<? super T> action) {  
        Objects.requireNonNull(action);  
        for (T t : this) {  
            action.accept(t);  
        }  
    }  
    
    default Spliterator<T> spliterator() {  
        return Spliterators.spliteratorUnknownSize(iterator(), 0);  
    }  
}
```

