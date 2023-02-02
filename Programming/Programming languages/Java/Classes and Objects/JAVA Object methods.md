02-02-2023
09:56
Authors: Tamerlan Khutuev
***
Tags: #stub #programming #java 
***
# Object methods
Класс Object является корнем иерархии классов.
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html

## getClass()
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#getClass()
Возвращает класс этого `Object`.

## hashCode()
Возвращает хэш объекта. Нужен чтобы с объектом могли работать хэш-таблицы (например, HashMap). Всегда должен предопределяться с equals().
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#hashCode()

## equals()
Возвращает результат сравнения объектов. Текущий объект сравнивается с объектом, который передается в параметр. По умолчанию в Object сравнивает ссылки через == :
```java
 public boolean equals(Object obj) {
     return (this == obj);
 }
```
Обязателен для переопределения вместе с hashCode(). Переопределенный метод должен возвращать true, если объекты логически равны.

Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#equals(java.lang.Object)

## clone()
Возвращает shallow (поверхностную) копию объекта. Для использования обязательно д.б. переопределен в классе. Класс должен имплементить маркерный интерфейс Cloneable, иначе метод выкинет CloneNotSupportedException. Типовая реализация:
```java
public YourClass clone() { 
    return (YourClass) super.clone(); 
}
```
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#clone()

## toString()
Возвращает строковое представление объекта. Реализация в Object:
```java
 getClass().getName() + '@' + Integer.toHexString(hashCode())
```
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#toString()

## notify()
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#notify()

## notifyAll()
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#notifyAll()

## wait(long timeout)
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#wait()

## finalize()
Docs: https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#finalize()
Устарело.
Вызывается, когда больше нет причин для того, чтобы объект был доступен из любого живого потока.


