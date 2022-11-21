17-11-2022
10:51
***
Tags: #programming #java 
***
# Лямбда-выражения

Функциональный интерфейс - это интерфейс который содержит только один метод. 
Аннотация @FunctionalInterface  не позволяет нам добавить больше одного метода. 

```java
import java.lang.FunctionalInterface; 
@FunctionalInterface 
public interface MyInterface{ 
	// один абстрактный метод 
	double sum(int a, int b); 
}
```

Синтаксис: 
```java
(parameter list) -> lambda body
```

Как и в js если тело состоит из одной строки - то можно не писать return.

```java
MyInterface a = (a, b) -> a + b 
```

На реальном примере. На сортировке. Для сортировки коллекций используется метод `Collections.sort(коллекция, компаратор);`.  Компоратор - это объект с имплементацией интерфейса **`Comparator`**. И что бы использовать это в сортировке - мы можем создать новый свой класс и имплементировать интерфейс **`Comparator`**, но для уменьшения кода мы можем использовать лямбды. 

```java
Comparator<String> comparator = (String obj1, String obj2) -> 
{ 
	return obj1.length() – obj2.length(); 
};

Collections.sort(list, comparator);
```

Можно сделать ещё короче
```java
Collections.sort(list, (obj1, obj2) -> obj1.length() — obj2.length() );
```