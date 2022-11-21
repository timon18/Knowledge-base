04-04-2022
11:50
***
Tags: #javascript 
***
# JS Context
Контекст указывает как функция была вызвана (указывает на this).
## this
This указывает на тот объект в контексте которого оно было вызвано.
Оно динамично и будет указывать на объект из которого оно было вызвано. 
```javascript
function hello() {
	console.log('Hello', this)
}

hello() // Вызываем функцию

// В браузере  this  указывает на глобальный объект Window
//(если он не вызван в другом объекте)
//в nodejs свой глобальный объект кстати
Hello 
Window {0: Window, 1: Window, window: Window, self: Window, document: document, name: '', location: Location, …}

const person = {
	name: "Max",
	sayHello: hello //та функция выше
}

person // внутри {name: "Max", sayHello: ƒ}

person.sayHello() 
//Как мы видим this теперь указывает на объект person
Hello
{name: "Max", sayHello: ƒ}
```

## call apply bind
Эти ключевые слова используются для передачи в функцию контекста и вызова функции с этим контекстом. 
```javascript
const person = {
	name: "Max",
	logInfo : function(job) {
		console.log(`Name is ${this.name}`)
		console.log(`Jib is ${job}`)
	}
}

person.logInfo() // Name is Max

//создадим новый объект
const lena = {
	name: 'Elena'
}

//И теперь вызововим метод объекта person с контекстом объекта lena

//bind передаёт в функцию контекст объекта lena
//и возврашает новую функцию
//Первым параметром принимает объект контекста 
//и следующими параметрами принимает аргументы которые переаются в функцию
const LenaInfoLog = person.logInfo.bind(lena, 'Backend')
LenaInfoLog()
//Name if Elena
//Job is Backend

//так же как и bind но сразу вызвает функцию
person.logInfo.call(lena, 'Backend')
//Name if Elena
//Job is Backend

//так же как и call но принимает вторым параметром массив аргументов
person.logInfo.apply(lena, ['Backend'])
//Name if Elena
//Job is Backend
```

##  Пример с использованием this и  prototype
К примеру если нас надо создать метод у массива который будет умножать каждый элемент на какое то число. Можно создать просто функцию, но если придётся часто использовать данный метод то будет легче если у всех массивов будет данный метод.
Про прототипы -> [[JS Prototype]]  
```javascript
cosnt array = [1, 2, 3, 4, 5]

Array.prototype.multBy = function(n) {
	return this.map(function(i) {
	return i* n})
}

array.multBy(20)
//[20, 40, 60, 80, 100]
```