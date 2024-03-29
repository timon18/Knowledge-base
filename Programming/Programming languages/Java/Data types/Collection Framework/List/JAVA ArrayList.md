31-01-2023
12:21
Authors: Khutuev Tamerlan.
***
Tags: #java #programming #collections_framework 
***
# ArrayList
ArrayList - является реализацией динамического массива объектов. 
Он ведёт себя как и обычный массив, но при переполнении удваивается в полтора раза (исходный массив копируется в массив по больше). Это удвоение немного дорогое и по этому лучше в конструкторе сразу указывать размер если можно. 

— Доступ к элементам по значению за линейное время O(n);  
— Медленный, когда вставляются и удаляются элементы из «середины» списка;  
— Позволяет хранить любые значения в том числе и null;  
— Не синхронизирован.

Хорошая статья: https://habr.com/ru/post/128269/

Реализует интерфейс List [[JAVA List (interface)]].
Docs: https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html