28-03-2023
11:14
Authors: Tamerlan Khutuev
***
Tags: #stub #patterns 
***
# Итератор
Также известен как: Cursor, Курсор

>**Итератор** — это поведенческий паттерн проектирования, который даёт возможность последовательно обходить элементы составных объектов, не раскрывая их внутреннего представления.
>https://refactoring.guru/ru/design-patterns/iterator

>Предоставляет способ последовательного обращения ко всем элементам составного объекта без раскрытия его внутреннего представления.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

## Проблема
Когда у нас есть коллекция объектов и мы хотим обходить ее элементы, может быть неудобно и опасно делать это вручную, особенно если коллекция изменяется во время итерации.

>Составной объект, скажем, список, должен предоставлять способ доступа к своим элементам, не раскрывая их внутреннюю структуру. Более того, иногда требуется обходить список по-разному в зависимости от решаемой задачи. Но вряд ли вы захотите засорять интерфейс класса List операциями для различных вариантов обхода, даже если все их можно предусмотреть заранее. Кроме того, иногда бывает нужно, чтобы в один и тот же момент действовало несколько активных обходов списка.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

## Решение
Паттерн Итератор предлагает создание объекта итератора, который инкапсулирует доступ к элементам коллекции и предоставляет удобный интерфейс для обхода этих элементов. Клиентский код получает итератор от коллекции и использует его для доступа к элементам, не заботясь о деталях доступа к коллекции.


## Пример

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class Book {
    private String title;
    private String author;
    private int year;

    public Book(String title, String author, int year) {
        this.title = title;
        this.author = author;
        this.year = year;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public int getYear() {
        return year;
    }
}

public class BookCollection implements Iterable<Book> {
    private List<Book> books;

    public BookCollection() {
        books = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
    }

    public void removeBook(Book book) {
        books.remove(book);
    }

    public Iterator<Book> iterator() {
        return new BookIterator();
    }

    private class BookIterator implements Iterator<Book> {
        private int currentIndex = 0;

        public boolean hasNext() {
            return currentIndex < books.size();
        }

        public Book next() {
            return books.get(currentIndex++);
        }

        public void remove() {
            books.remove(--currentIndex);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        BookCollection collection = new BookCollection();
        collection.addBook(new Book("The Catcher in the Rye", "J.D. Salinger", 1951));
        collection.addBook(new Book("To Kill a Mockingbird", "Harper Lee", 1960));
        collection.addBook(new Book("1984", "George Orwell", 1949));

        Iterator<Book> iterator = collection.iterator();
        while (iterator.hasNext()) {
            Book book = iterator.next();
            System.out.println(book.getTitle() + " by " + book.getAuthor() + ", " + book.getYear());
        }
    }
}
```