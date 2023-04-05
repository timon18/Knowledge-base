05-04-2023
13:31
Authors: Белоусов Даниил
***
Tags: #stub #es6 #tdz
***
# Temporal Dead Zone


"Temporal Dead Zone" (TDZ) - это поведение, связанное с использованием переменных let и const в ES6. Когда переменная объявляется с помощью let или const, она создается во время компиляции, но нельзя обратиться к ней до тех пор, пока не будет выполнено объявление переменной. В этом случае переменная находится в "Temporal Dead Zone". Если вы попытаетесь обратиться к переменной до ее объявления, вы получите ошибку ReferenceError.

На практике это может выглядеть так:

```
console.log(myVar); // ReferenceError!

let myVar = 42;
```

В этом коде мы пытаемся обратиться к переменной `myVar` до ее объявления, что приводит к ошибке. Чтобы избежать этого, всегда объявляйте переменные перед их использованием.