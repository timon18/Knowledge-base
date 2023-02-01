31-01-2023
12:21
Authors: Khutuev Tamerlan.
***
Tags: #java #programming #collections_framework 
***
# LinkedList
LinkedList - это двунаправленный список, где каждый элемент содержит указатель на следующий и предыдущий элемент. (как я понял он используется редко. в статье ниже в комментариях есть обсуждение)

![](https://habrastorage.org/r/w1560/storage1/6605581f/f23b97d5/f4c7c489/843a7bbc.png)

— Из LinkedList можно организовать стэк, очередь, или двойную очередь, со временем доступа O(1);  
— На вставку и удаление из середины списка, получение элемента по индексу или значению потребуется линейное время O(n). Однако, на добавление и удаление из середины списка, используя ListIterator.add() и ListIterator.remove(), потребуется O(1);  
— Позволяет добавлять любые значения в том числе и null. Для хранения примитивных типов использует соответствующие классы-оберки;  
— Не синхронизирован.

Хорошая статься: https://habr.com/ru/post/127864/

Реализует интерфейс List [[JAVA List (interface)]] и Deque [[JAVA Deque (interface)]].
Docs: https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html