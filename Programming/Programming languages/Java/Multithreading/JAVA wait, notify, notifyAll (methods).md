07-03-2023
10:44
Authors: Tamerlan Khutuev
***
Tags: #stub #java #programming 
***
# wait, notify, notifyAll
![[Java_-_Wait_and_Notify.webp]]
## wait
_Действия ожидания_ происходят при вызове `wait()`, или временных форм `wait(long millisecs)` и `wait(long millisecs, int nanosecs)`.

Метод wait можно вызвать у объекта-монитора ([[JAVA Monitor]]) и только когда этот монитор занять (если он внутри блока **synchronized**). [[JAVA Synchronized]]
Этот метод заставляет поток ждать пока какой либо другой поток не вызвовет notify или notifyAll.

JAVA Specs: https://docs.oracle.com/javase/specs/jls/se19/html/jls-17.html#jls-17.2.1

## notify, notifyAll
Действия уведомления происходят при вызове методов `notify` и `notifyAll`.
Эти методы используются для пробуждения ждущих потоков. notify уведомляет любой из них, а notifyAll уведомляет все ждущие потоки. 

JAVA Specs: https://docs.oracle.com/javase/specs/jls/se19/html/jls-17.html#jls-17.2.2