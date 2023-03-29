28-03-2023
10:43
Authors: Eloev Georgiy 
***
Tags: #stub #patterns 
***
# Абстрактная фабрика


>Предоставляет интерфейс для создания семейств взаимосвязанных или взаимозависимых объектов, не специфицируя их конкретных классов.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

>**Абстрактная фабрика** — это порождающий паттерн проектирования, который позволяет создавать семейства связанных объектов, не привязываясь к конкретным классам создаваемых объектов.
>(https://refactoring.guru/ru/design-patterns/abstract-factory)


## Проблема.
Когда необходимо создать группу связанных объектов, может быть неудобно и неэффективно создавать каждый объект по отдельности, особенно когда эти объекты имеют много общих свойств и зависят от определенных параметров.

## Решение

Паттерн Abstract Factory предлагает создание интерфейса Factory, который определяет методы для создания связанных объектов. Каждая конкретная реализация фабрики реализует интерфейс Factory и создает связанные объекты определенного типа. Таким образом, клиентский код может создавать объекты группы без необходимости знать их конкретную реализацию.

## Пример

```java
// Интерфейсы для кнопок и фонов
public interface Button {
    void render();
}

public interface Background {
    void render();
}

// Реализации кнопок и фонов
public class ButtonTheme1 implements Button {
    public void render() {
        System.out.println("Button Theme 1");
    }
}

public class ButtonTheme2 implements Button {
    public void render() {
        System.out.println("Button Theme 2");
    }
}

public class BackgroundTheme1 implements Background {
    public void render() {
        System.out.println("Background Theme 1");
    }
}

public class BackgroundTheme2 implements Background {
    public void render() {
        System.out.println("Background Theme 2");
    }
}

// Фабрики для каждой темы
public interface ThemeFactory {
    Button createButton();
    Background createBackground();
}

public class Theme1Factory implements ThemeFactory {
    public Button createButton() {
        return new ButtonTheme1();
    }

    public Background createBackground() {
        return new BackgroundTheme1();
    }
}

public class Theme2Factory implements ThemeFactory {
    public Button createButton() {
        return new ButtonTheme2();
    }

    public Background createBackground() {
        return new BackgroundTheme2();
    }
}
```