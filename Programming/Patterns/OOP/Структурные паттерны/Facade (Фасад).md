28-03-2023
11:09
Authors: Tamerlan Khutuev
***
Tags: #stub #patterns 
***
# Фасад
https://refactoring.guru/ru/design-patterns/facade

Паттерн фасад (Facade) позволяет скрыть сложность системы и предоставить простой интерфейс для взаимодействия с ней. Фасад предоставляет единый интерфейс для группы интерфейсов в системе.

## Проблема.
В большом приложении часто бывает так, что есть сложные подсистемы, которые взаимодействуют между собой. Иногда клиенту приложения не нужно знать обо всех этих сложностях и просто нужен удобный интерфейс для работы с подсистемами. Кроме того, если подсистемы изменятся, это может повлиять на клиентский код.

## Решение
Паттерн Facade (Фасад) - это структурный паттерн проектирования, который предоставляет упрощенный интерфейс для работы с сложной подсистемой, скрывая ее детали реализации. То есть, вместо того чтобы клиентский код работал с каждой подсистемой напрямую, он будет использовать только один объект-фасад, который обращается к нужным объектам внутри себя.

## Пример
```java
// Компоненты подсистемы
class CPU {
    public void freeze() { /*...*/ }
    public void jump(long position) { /*...*/ }
    public void execute() { /*...*/ }
}

class Memory {
    public void load(long position, byte[] data) { /*...*/ }
}

class HardDrive {
    public byte[] read(long lba, int size) { /*...*/ }
}

// Фасад
class Computer {
    private CPU cpu;
    private Memory memory;
    private HardDrive hardDrive;

    public Computer() {
        this.cpu = new CPU();
        this.memory = new Memory();
        this.hardDrive = new HardDrive();
    }

    public void startComputer() {
        cpu.freeze();
        memory.load(0x00000000, hardDrive.read(0x00000000, 1024));
        cpu.jump(0x00000000);
        cpu.execute();
    }
}

// Клиентский код
class Client {
    public static void main(String[] args) {
        Computer computer = new Computer();
        computer.startComputer();
    }
}
```
В этом примере классы `CPU`, `Memory` и `HardDrive` являются компонентами подсистемы. Фасад `Computer` скрывает сложность этих компонентов и предоставляет единый интерфейс `startComputer()` для запуска компьютера. Клиентский код использует этот единый интерфейс, не заботясь о том, как работает подсистема внутри.
