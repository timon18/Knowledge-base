28-03-2023
10:43
Authors: Eloev Georgiy 
***
Tags: #stub #patterns 
***
# Прототип
Также известен как: Клон, Prototype

Паттерн Prototype - это паттерн проектирования, который позволяет создавать копии существующих объектов, не зависимо от их типа и сложности.

Суть паттерна заключается в создании прототипа объекта, который будет использоваться для создания копий. Обычно прототип создается путем клонирования существующего объекта. Клонирование может быть глубоким или поверхностным, в зависимости от того, какие свойства объекта должны быть скопированы.

>**Прототип** — это порождающий паттерн проектирования, который позволяет копировать объекты, не вдаваясь в подробности их реализации.
>(https://refactoring.guru/ru/design-patterns/prototype)

>Задает виды создаваемых объектов с помощью экземпляра-прототипа и создает новые объекты путем копирования этого прототипа.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

## Проблема
Паттерн Prototype используется, когда требуется создать новый объект, используя существующий объект в качестве прототипа, т.е. копировать объекты. Это может быть полезно, когда создание объекта требует больших затрат ресурсов, например, при создании объектов базы данных.

## Решение
Паттерн Prototype решает эту проблему, создавая прототип объекта, который может быть скопирован для создания нового объекта. Для этого используется метод clone(), который создает копию объекта, без необходимости создания нового объекта "с нуля".

## Пример

```java
abstract class Shape implements Cloneable {
    private String id;
    protected String type;

    abstract void draw();

    public String getType() {
        return type;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public Object clone() {
        Object clone = null;

        try {
            clone = super.clone();
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }

        return clone;
    }
}

class Circle extends Shape {

    public Circle() {
        type = "Circle";
    }

    @Override
    void draw() {
        System.out.println("Inside Circle::draw() method.");
    }
}

class Square extends Shape {

    public Square() {
        type = "Square";
    }

    @Override
    void draw() {
        System.out.println("Inside Square::draw() method.");
    }
}

class ShapeCache {

    private static Hashtable<String, Shape> shapeMap = new Hashtable<String, Shape>();

    public static Shape getShape(String shapeId) {
        Shape cachedShape = shapeMap.get(shapeId);
        return (Shape) cachedShape.clone();
    }

    // Загрузка настроек
    public static void loadCache() {
        Circle circle = new Circle();
        circle.setId("1");
        shapeMap.put(circle.getId(), circle);

        Square square = new Square();
        square.setId("2");
        shapeMap.put(square.getId(), square);
    }
}
```