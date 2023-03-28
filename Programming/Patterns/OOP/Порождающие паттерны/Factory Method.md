28-03-2023
10:43
Authors: Eloev Georgiy 
***
Tags: #stub #patterns 
***
# Фабричный метод
Также известен как: Виртуальный конструктор, Factory Method

Паттерн Factory Method - это порождающий паттерн проектирования, который определяет интерфейс для создания объектов, но позволяет подклассам выбирать классы, которые должны быть созданы.

>Определяет интерфейс для создания объекта, но оставляет подклас- сам решение о том, экземпляры какого класса должны создаваться. Фаб- ричный метод позволяет классу делегировать создание экземпляров под- классам.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

>**Фабричный метод** — это порождающий паттерн проектирования, который определяет общий интерфейс для создания объектов в суперклассе, позволяя подклассам изменять тип создаваемых объектов.
>(https://refactoring.guru/ru/design-patterns/factory-method)

## Проблема
В разработке программного обеспечения часто возникает необходимость создания объектов определенных классов в разных местах приложения. Каждый раз создавать объекты напрямую может быть неэффективно и неудобно в поддержке.


## Решение
Паттерн Factory Method предлагает использовать один общий метод для создания объектов, называемый "фабричным методом". Фабричный метод определяет интерфейс для создания объектов, но позволяет подклассам выбирать класс для создания. Таким образом, объекты могут быть созданы в единой точке, а создание новых объектов становится более гибким и удобным в поддержке.

## Пример

```java
interface Transport {
    void deliver();
}

class Car implements Transport {

    @Override
    public void deliver() {
        System.out.println("The car is delivering the goods.");
    }
}

class Ship implements Transport {

    @Override
    public void deliver() {
        System.out.println("The ship is delivering the goods.");
    }
}

abstract class TransportFactory {

    public void planDelivery() {
        Transport transport = createTransport();
        transport.deliver();
    }

    protected abstract Transport createTransport();
}

class RoadLogistics extends TransportFactory {

    @Override
    protected Transport createTransport() {
        return new Car();
    }
}

class SeaLogistics extends TransportFactory {

    @Override
    protected Transport createTransport() {
        return new Ship();
    }
}
```