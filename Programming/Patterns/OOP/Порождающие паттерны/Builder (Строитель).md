17-01-2023
12:23
Authors: Eloev Georgiy 
***
Tags: #stub #patterns 
***
# Строитель

Паттерн Builder - это порождающий паттерн проектирования, который позволяет создавать объекты сложной структуры поэтапно, не загромождая код клиента множеством конструкторов.

Суть паттерна заключается в том, что есть класс-строитель (Builder), который определяет интерфейс для создания объекта. Затем есть конкретные строители (Concrete Builders), которые реализуют этот интерфейс и предоставляют методы для поэтапного создания объекта. Клиент использует объект директора (Director), который управляет процессом создания объекта, вызывая методы строителя в правильном порядке, чтобы создать объект нужной структуры.

>Отделяет конструирование сложного объекта от его представления, так что в результате одного и того же процесса конструирования могут получаться разные представления.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

>**Строитель** — это порождающий паттерн проектирования, который позволяет создавать сложные объекты пошагово. Строитель даёт возможность использовать один и тот же код строительства для получения разных представлений объектов.
>(https://refactoring.guru/ru/design-patterns/builder)

## Проблема

При создании сложных объектов, конструкторы могут содержать большое количество параметров, что делает их использование неудобным и трудным для чтения. Кроме того, такой подход не позволяет легко создавать объекты с различными комбинациями параметров.

## Решение

Паттерн Builder предлагает вынести процесс создания объекта в отдельный класс-строитель (Builder), который позволяет создавать объекты поэтапно, задавая только необходимые параметры. Это упрощает создание объектов и позволяет легко создавать объекты с различными комбинациями параметров.

## Пример

```java
public class Computer {
    private String cpu;
    private String gpu;
    private int ram;
    private int storage;
    private String os;

    private Computer(String cpu, String gpu, int ram, int storage, String os) {
        this.cpu = cpu;
        this.gpu = gpu;
        this.ram = ram;
        this.storage = storage;
        this.os = os;
    }

    public static class Builder {
        private String cpu;
        private String gpu;
        private int ram;
        private int storage;
        private String os;

        public Builder cpu(String cpu) {
            this.cpu = cpu;
            return this;
        }

        public Builder gpu(String gpu) {
            this.gpu = gpu;
            return this;
        }

        public Builder ram(int ram) {
            this.ram = ram;
            return this;
        }

        public Builder storage(int storage) {
            this.storage = storage;
            return this;
        }

        public Builder os(String os) {
            this.os = os;
            return this;
        }

        public Computer build() {
            return new Computer(cpu, gpu, ram, storage, os);
        }
    }
}
```