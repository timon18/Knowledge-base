09-11-2022
11:09
***
Tags: #programming #java 
***
# String

Строки в java являются объектами и хранятся в куче ([[JAVA Heap]]). 
Строки являются неизменяемыми (immutable). 

Создание строк:
```java 
String a = "Hello"; //Строка-константа
// или
String a = new String("Hello");
```

При создании строк констант java автоматически из интернирует ([[JAVA Interning]]) и по этому при сравнении через `==` они будут равны (`==` сравнивает только ссылки).
При создании они будут разными см. ([[JAVA Interning]]) и для сравнения используется метод `.equals()` который сравнивает содержимое строк.
```java
String a = "123";  
String c = new String("123");  
System.out.println(a==c);        //False  
System.out.println(a.equals(c)); //True
```
