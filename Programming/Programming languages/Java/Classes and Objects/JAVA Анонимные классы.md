10-11-2022
14:26
***
Tags: #programming #java 
***
# Анонимные классы

Анонимные классы - это подвид внутренних/вложенных классов. ([[JAVA Вложенные классы]]).

Пример создания:
```java
public interface MonitoringSystem { 
	public void startMonitoring(); 
}

public class Main { 
	public static void main(String[] args) { 
		MonitoringSystem generalModule = new MonitoringSystem() { 
		@Override public void startMonitoring() { 
			System.out.println("Мониторинг общих показателей стартовал!"); 
		} 
	}; 
	generalModule.startMonitoring();  
	} 
}
```

В тот момент, когда мы пишем :
```java
MonitoringSystem generalModule = new MonitoringSystem() { 
	//код
};
```
внутри java:
1. Создается безымянный Java-класс, реализующий интерфейс `MonitoringSystem`.
2. Создается один объект этого класса.

У анонимных классов нет конструктора, но можно использовать блоки инициализации ([[JAVA Блоки инициализации]]).