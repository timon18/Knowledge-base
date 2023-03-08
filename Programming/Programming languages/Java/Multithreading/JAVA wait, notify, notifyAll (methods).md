07-03-2023
10:44
Authors: Tamerlan Khutuev
***
Tags: #stub #java #programming 
***
# wait, notify, notifyAll

## wait
_Действия ожидания_ происходят при вызове `wait()`, или временных форм `wait(long millisecs)` и `wait(long millisecs, int nanosecs)`.

Метод wait можно вызвать у объекта-монитора и только когда этот монитор занять (если он внутри блока **synchronized**). [[JAVA wait, notify, notifyAll (methods) | synchronized]]

JAVA Specs: https://docs.oracle.com/javase/specs/jls/se19/html/jls-17.html#jls-17.2.1

## notify, notifyAll
Действия уведомления происходят при вызове методов `notify` и `notifyAll`.

JAVA Specs: https://docs.oracle.com/javase/specs/jls/se19/html/jls-17.html#jls-17.2.2