08-03-2023
16:49
Authors: Tamerlan Khutuev
***
Tags: #stub #java #programming 
***
# Wait Sets
Каждый объект, помимо связанного монитора, имеет связанный _набор ожидания_. Набор ожидания — это набор потоков.

Когда объект создается впервые, его набор ожидания пуст. Элементарные действия, которые добавляют потоки в наборы ожидания и удаляют потоки из наборов ожидания, являются атомарными. Наборы ожидания обрабатываются исключительно с помощью методов `Object`.``wait, Object``.``notify и Object``.``notifyAll.
[[JAVA wait, notify, notifyAll (methods)]]

JAVA Spec: https://docs.oracle.com/javase/specs/jls/se19/html/jls-17.html#jls-17.2

![[java-monitor 1.gif]]
