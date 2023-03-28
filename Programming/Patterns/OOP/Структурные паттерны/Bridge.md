28-03-2023
11:07
Authors: 
***
Tags: #stub #patterns 
***
# Мост
Шаблон моста — это структурный шаблон проектирования, который позволяет отделить абстракцию от ее реализации, чтобы они могли изменяться независимо друг от друга. Он включает в себя создание двух отдельных иерархий, одну для абстракции и одну для реализации, а затем использование композиции для их объединения. Этот шаблон способствует слабой связи и разделению задач, а также позволяет легко расширять и модифицировать как абстракцию, так и реализацию.

## Проблема.
Необходимо разделить абстракцию и реализацию, чтобы они могли изменяться независимо друг от друга. Это позволяет легко добавлять новые реализации, не влияя на клиентский код.

## Решение
Паттерн Bridge решает эту проблему, создавая две иерархии классов: абстракцию и реализацию. Абстракция определяет интерфейс для клиентского кода, а реализация предоставляет конкретные реализации этого интерфейса. Абстракция содержит ссылку на реализацию, которая может быть установлена во время выполнения. Это позволяет клиентскому коду работать с абстракцией, не зная о конкретной реализации.

## Пример
```java
// Абстракция
abstract class Shape {
    protected Color color;

    public Shape(Color color) {
        this.color = color;
    }

    abstract public void draw();
}

// Реализация
interface Color {
    public void applyColor();
}

// Конкретная реализация
class Red implements Color {
    public void applyColor() {
        System.out.println("Red color applied");
    }
}

// Конкретная реализация
class Blue implements Color {
    public void applyColor() {
        System.out.println("Blue color applied");
    }
}

// Конкретная реализация
class Green implements Color {
    public void applyColor() {
        System.out.println("Green color applied");
    }
}

// Конкретная абстракция
class Circle extends Shape {
    public Circle(Color color) {
        super(color);
    }

    public void draw() {
        System.out.print("Circle drawn. ");
        color.applyColor();
    }
}

// Конкретная абстракция
class Square extends Shape {
    public Square(Color color) {
        super(color);
    }

    public void draw() {
        System.out.print("Square drawn. ");
        color.applyColor();
    }
}

// Использование
public class BridgeExample {
    public static void main(String[] args) {
        Shape circle = new Circle(new Red());
        circle.draw();

        Shape square = new Square(new Blue());
        square.draw();

        Shape square2 = new Square(new Green());
        square2.draw();
    }
}
```
В этом примере класс "Shape" представляет абстракцию, а класс "Color" представляет реализацию. Классы "Circle" и "Square" являются конкретными абстракциями, а классы "Red", "Blue" и "Green" являются конкретными реализациями