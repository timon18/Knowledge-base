08-03-2023
16:56
Authors: Tamerlan Khutuev
***
Tags: #stub #java #programming 
***
# interrupt
Действия прерывания происходят при вызове `Thread.interrupt`, а также методов, определенных для его вызова по очереди, таких как `ThreadGroup.interrupt`.

Метод вызваеться для прерывания потока. Если поток находится в спящем или ожидающем состоянии - то interrupt прервёт выполнение потока бросив InterruptedException.

Если поток не находится в спящем или оджидающем режиме - то вызов метода просто установит флаг прервывания в true. 

JAVA Specs: https://docs.oracle.com/javase/specs/jls/se19/html/jls-17.html#jls-17.2.3