28-03-2023
11:09
Authors: Tamerlan Khutuev
***
Tags: #stub #patterns 
***
# Декоратор
Также известен как: Wrapper, Обёртка, Decorator

>**Декоратор** — это структурный паттерн проектирования, который позволяет динамически добавлять объектам новую функциональность, оборачивая их в полезные «обёртки».
>(https://refactoring.guru/ru/design-patterns/decorator)

>Динамически добавляет объекту новые обязанности. Является гибкой альтернативой порождению подклассов с целью расширения функциональности.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

## Проблема.
В процессе разработки программного обеспечения может возникнуть необходимость добавления новых функций к существующему классу, но без изменения его исходного кода или наследования нового класса от существующего. Требуется создать новый класс, который бы расширял функциональность существующего класса, но при этом сохранял его интерфейс и поведение.

## Решение
Паттерн Decorator предлагает создать новый класс-декоратор, который будет оборачивать существующий класс, расширяя его функциональность. Декоратор имеет тот же интерфейс, что и оборачиваемый класс, и может вызывать его методы, при этом добавляя свою логику в их выполнение. Таким образом, декоратор динамически добавляет новую функциональность к объекту без изменения его исходного кода.

## Пример
Предположим, у нас есть интерфейс "Кофе" (Coffee), который определяет методы для приготовления кофе. У нас также есть класс "Обычный кофе" (SimpleCoffee), который реализует этот интерфейс и представляет собой простой кофе без добавок. Мы хотим добавить возможность добавления молока и сахара к кофе, не изменяя исходный код класса "Обычный кофе". Мы можем создать два класса-декоратора: "Кофе с молоком" (CoffeeWithMilk) и "Кофе с молоком и сахаром" (CoffeeWithMilkAndSugar).
```java
interface Coffee {
    double getCost();
    String getDescription();
}

class SimpleCoffee implements Coffee {
    public double getCost() {
        return 1.0;
    }
    
    public String getDescription() {
        return "Простой кофе";
    }
}

class CoffeeWithMilk implements Coffee {
    private Coffee coffee;
    
    public CoffeeWithMilk(Coffee coffee) {
        this.coffee = coffee;
    }
    
    public double getCost() {
        return coffee.getCost() + 0.5;
    }
    
    public String getDescription() {
        return coffee.getDescription() + ", с молоком";
    }
}

class CoffeeWithMilkAndSugar implements Coffee {
    private Coffee coffee;
    
    public CoffeeWithMilkAndSugar(Coffee coffee) {
        this.coffee = coffee;
    }
    
    public double getCost() {
        return coffee.getCost() + 0.3;
    }
    
    public String getDescription() {
        return coffee.getDescription() + ", с молоком и сахаром";
    }
}
```
Здесь классы `CoffeeWithMilk` и `CoffeeWithMilkAndSugar` являются декораторами, которые оборачивают объекты типа `Coffee` (в данном случае - объект типа `SimpleCoffee`). Классы-декораторы расширяют функциональность объект
