06-03-2023
08:53
Authors: Tamerlan Khutuev
***
Tags: #stub #java #programming 
***
# Concurrent Collections
**Concurrent Collections** — набор коллекций, более эффективно работающие в многопоточной среде нежели стандартные универсальные коллекции из java.util пакета. Вместо базового враппера Collections.synchronizedList с блокированием доступа ко всей коллекции используются блокировки по сегментам данных или же оптимизируется работа для параллельного чтения данных по [wait-free](https://web.archive.org/web/20220427140138/http://ru.wikipedia.org/wiki/%D0%9D%D0%B5%D0%B1%D0%BB%D0%BE%D0%BA%D0%B8%D1%80%D1%83%D1%8E%D1%89%D0%B0%D1%8F_%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F) алгоритмам.

- [[JAVA ConcurrentHashMap]]
- [[JAVA CopyOnWriteArrayList]]
- [[JAVA CopyOnWriteArraySet]]
- [[JAVA BlockingQueue]]
- [[JAVA BlockingDeque]]
- [[JAVA ConcurrentSkipListMap]]
- [[JAVA ConcurrentSkipListSet]]

![Java Concurrent Collections Cheat Sheet](https://www.logicbig.com/tutorials/core-java-tutorial/java-collections/concurrent-collection-cheatsheet/images/collection-imp.png)


