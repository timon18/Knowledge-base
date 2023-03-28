28-03-2023
11:07
Authors: 
***
Tags: #stub #patterns 
***
# Мост
Шаблон моста — это структурный шаблон проектирования, который позволяет отделить абстракцию от ее реализации, чтобы они могли изменяться независимо друг от друга. Он включает в себя создание двух отдельных иерархий, одну для абстракции и одну для реализации, а затем использование композиции для их объединения. Этот шаблон способствует слабой связи и разделению задач, а также позволяет легко расширять и модифицировать как абстракцию, так и реализацию.

## Проблема.


## Решение


## Пример
```java
interface DrawingAPI {
    public void drawCircle(double x, double y, double radius);
}

class DrawingAPI1 implements DrawingAPI {
    @Override
    public void drawCircle(double x, double y, double radius) {
        System.out.printf("API1.circle at %f:%f radius %f\n", x, y, radius);
    }
}

class DrawingAPI2 implements DrawingAPI {
    @Override
    public void drawCircle(double x, double y, double radius) {
        System.out.printf("API2.circle at %f:%f radius %f\n", x, y, radius);
    }
}

abstract class Shape {
    protected DrawingAPI drawingAPI;

    protected Shape(DrawingAPI drawingAPI) {
        this.drawingAPI = drawingAPI;
    }

    public abstract void draw();
    public abstract void resizeByPercentage(double pct);
}

class CircleShape extends Shape {
    private double x, y, radius;

    public CircleShape(double x, double y, double radius, DrawingAPI drawingAPI) {
        super(drawingAPI);
        this.x = x;
        this.y = y;
        this.radius = radius;
    }

    public void draw() {
        drawingAPI.drawCircle(x, y, radius);
    }

    public void resizeByPercentage(double pct) {
        radius *= (1.0 + pct/100.0);
    }
}

public class Main {
    public static void main(String[] args) {
        Shape[] shapes = new Shape[] {
                new CircleShape(1, 2, 3, new DrawingAPI1()),
                new CircleShape(5, 7, 11, new DrawingAPI2())
        };

        for (Shape shape : shapes) {
            shape.resizeByPercentage(2.5);
            shape.draw();
        }
    }
}
```
В этом примере шаблон моста используется для отделения абстрактного класса Shape от его различных конкретных реализаций (в данном случае CircleShape) и DrawingAPI, который используется для рисования фигуры. Класс Shape содержит ссылку на объект DrawingAPI, и этот объект используется для делегирования рисования фигуры. Разделив абстракции Shape и DrawingAPI, мы можем создавать новые фигуры или новые DrawingAPI независимо друг от друга, а любую новую комбинацию Shape и DrawingAPI можно создать, просто создав новый подкласс Shape и передав ему новый экземпляр DrawingAPI.