28-03-2023
11:17
Authors: Tamerlan Khutuev
***
Tags: #stub #patterns 
***
# Шаблонный метод

>**Шаблонный метод** — это поведенческий паттерн проектирования, который определяет скелет алгоритма, перекладывая ответственность за некоторые его шаги на подклассы. Паттерн позволяет подклассам переопределять шаги алгоритма, не меняя его общей структуры.
>https://refactoring.guru/ru/design-patterns/template-method

>Шаблонный метод определяет основу алгоритма и позволяет подклассам переопределить некоторые шаги алгоритма, не изменяя его структуру в целом.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

## Проблема
Иногда бывает необходимо добавить новую функциональность в классы, которые уже созданы и используются в программе, но изменять эти классы нежелательно или невозможно. Также может возникнуть необходимость применить некоторую операцию ко всем элементам сложной структуры данных.

## Решение
Паттерн Visitor (Посетитель) - это поведенческий паттерн проектирования, который позволяет добавлять новые операции к классам объектов без изменения этих классов. Также данный паттерн позволяет применять операцию ко всем элементам сложной структуры данных, не изменяя сами элементы.

## Пример
Рассмотрим пример создания редактора графических документов с помощью паттерна Visitor.
```java
// Интерфейс для элементов графического документа
interface Graphic {
    void accept(Visitor visitor);
}

// Класс "лист" дерева
class Rectangle implements Graphic {
    public void accept(Visitor visitor) {
        visitor.visitRectangle(this);
    }
}

// Класс "лист" дерева
class Circle implements Graphic {
    public void accept(Visitor visitor) {
        visitor.visitCircle(this);
    }
}

// Класс-контейнер для элементов графического документа
class CompoundGraphic implements Graphic {
    private List<Graphic> graphics = new ArrayList<>();

    public void add(Graphic graphic) {
        graphics.add(graphic);
    }

    public void accept(Visitor visitor) {
        for (Graphic graphic : graphics) {
            graphic.accept(visitor);
        }
        visitor.visitCompoundGraphic(this);
    }
}

// Интерфейс для посетителя
interface Visitor {
    void visitRectangle(Rectangle rectangle);

    void visitCircle(Circle circle);

    void visitCompoundGraphic(CompoundGraphic compoundGraphic);
}

// Реализация посетителя для отрисовки графических элементов
class DrawVisitor implements Visitor {
    public void visitRectangle(Rectangle rectangle) {
        System.out.println("Draw rectangle");
    }

    public void visitCircle(Circle circle) {
        System.out.println("Draw circle");
    }

    public void visitCompoundGraphic(CompoundGraphic compoundGraphic) {
        System.out.println("Draw compound graphic");
    }
}

// Реализация посетителя для вычисления площади графических элементов
class AreaVisitor implements Visitor {
    private double area = 0;

    public void visitRectangle(Rectangle rectangle) {
        area += 10;
    }

    public void visitCircle(Circle circle) {
        area += 20;
    }

    public void visitCompoundGraphic(CompoundGraphic compoundGraphic) {
        // Do nothing
    }

    public double getArea() {
        return area;
    }
}

// Клиентский код
public class Client {
    public static void main(String[] args) {
        CompoundGraphic graphic = new CompoundGraphic();
        graphic.add(new Rectangle());
        graphic.add(new Circle());

        graphic.accept(new DrawVisitor());

        AreaVisitor areaVisitor = new AreaVisitor();
        graphic.accept(areaVisitor);
        System.out.println("Area of graphic: " + areaVisitor.getArea

```
