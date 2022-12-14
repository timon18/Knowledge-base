09-11-2022
10:00
Authors: Khutuev Tamerlan.
***
Tags: #programming #java 
***
# Autoboxing and unboxing

## Autoboxing 
**Автоупаковка** - это автоматическая инкапсуляция примитивного типа в эквивалентную ему класс-обёртку. Когда переменной класса-обёртки мы присваиваем значение примитивного типа. 

**Класс-обёртка** - это специальный класс для хранения значения примитива. У каждого примитивного типа есть свой класс-обёртка. Они нужны в основном, что бы добавить методы к примитивным типом. 

Автоупаковка происходит:
- При присвоении значения примитивного типа переменой соответствующего класса-обёртки. 
```java
Integer iOb = new Integer(7); 
Double dOb = new Double(7.0); 
Character cOb = new Character('a'); 
Boolean bOb = new Boolean(true);
```
- При передаче примитивного типа в параметр метода, ожидающего соответствующий ему класс-обёртку. 
```java
public class Main { 
	public static void main(String[] args) { 
		method(new Integer(7)); 
	} 
	
	public static void method(Integer iOb) { 
	System.out.println("Integer"); 
	} 
}
```

---
## Unboxing
**Автораспаковка** - это преобразование класса-обёртки в соответствующий ему примитивный тип. Когда переменной примитивного типа можно присвоить объект класса-обёртки. 
```java
public class Main { 
	public static void main(String[] args) { 
		int x = 7; 
		Integer y = 111; 
		x = y; // автораспаковка 
		y = x * 123; // автоупаковка 
	} 
}	
```