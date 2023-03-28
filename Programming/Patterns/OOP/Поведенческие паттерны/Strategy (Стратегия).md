28-03-2023
11:17
Authors: Tamerlan Khutuev
***
Tags: #stub #patterns 
***
# Стратегия

>**Стратегия** — это поведенческий паттерн проектирования, который определяет семейство схожих алгоритмов и помещает каждый из них в собственный класс, после чего алгоритмы можно взаимозаменять прямо во время исполнения программы.
>https://refactoring.guru/ru/design-patterns/strategy

>Определяет семейство алгоритмов, инкапсулирует каждый из них и делает их взаимозаменяемыми. Стратегия позволяет изменять алгоритмы независимо от клиентов, которые ими пользуются.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

## Проблема
Иногда необходимо реализовать алгоритм, который может иметь несколько вариантов исполнения, которые могут меняться во время выполнения программы. При этом, варианты исполнения могут быть схожи, но различаться деталями. В такой ситуации возникает необходимость в разделении алгоритма на отдельные компоненты, что бы была возможность подмены компонента в зависимости от требований.

## Решение
Паттерн Strategy предлагает выделить семейство алгоритмов в отдельные классы, реализующие общий интерфейс. Таким образом, можно менять поведение объекта во время выполнения программы, просто переключая используемый объект-стратегию на другой, реализующий тот же интерфейс.

## Пример
Рассмотрим пример, где необходимо реализовать функцию, которая сортирует список объектов различными алгоритмами. Для этого мы создадим интерфейс Strategy и реализуем его двумя классами: QuickSort и MergeSort, которые будут представлять конкретные алгоритмы сортировки. Затем создадим класс Context, который будет использовать выбранный алгоритм для сортировки списка.

```java
import java.util.List;

interface SortStrategy {
    <T extends Comparable<T>> void sort(List<T> list);
}

class QuickSortStrategy implements SortStrategy {
    public <T extends Comparable<T>> void sort(List<T> list) {
        // реализация быстрой сортировки
    }
}

class MergeSortStrategy implements SortStrategy {
    public <T extends Comparable<T>> void sort(List<T> list) {
        // реализация сортировки слиянием
    }
}

class SortContext {
    private SortStrategy strategy;

    public SortContext(SortStrategy strategy) {
        this.strategy = strategy;
    }

    public <T extends Comparable<T>> void sort(List<T> list) {
        strategy.sort(list);
    }
}

// Использование:
List<Integer> list = new ArrayList<>(Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5));
SortContext context = new SortContext(new QuickSortStrategy());
context.sort(list); // список отсортирован быстрой сортировкой

context = new SortContext(new MergeSortStrategy());
context.sort(list); // список отсортирован сортировкой слиянием

```
