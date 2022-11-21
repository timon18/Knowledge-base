04-04-2022
11:19
***
Tags: #javascript 
***
# JS Prototype
Прототип это объект который присутствует у родительских объектов. Там типо находятся методы и свойства. 
Так же могут быть одинаковые поля и в объекте и в прототипе. В таком случае будет браться первый (на первом уровне). Ну типо JS будет искать в прототипе и если не нашёл то идет в следующий прототип  (прототип в прототипе) и т.д. (по цепочке)
```javascript
const person = new Object({
	name: "Max"
})

// Если попытатся вывести сейчас 
person.sayHello()
//будет ошибка так как у данного объекта нет такой функции

// Но мы можем расширить сам объект Object 
Object.prototype.sayHello = function() {
	console.log('Hello')
}

//КСТАТИ!!! Теперь у любой хрени (даже у строки) будет метод sayHello
//Так как строка это экземпляр объекта String который наследуется от Object

// И теперт в person есть метод sayHello
person.sayHello() // Hello!

//Теперь если попробывать вывести в консоли person

1.  {name: 'Max'}

1.  name: "Max"
2.  [[Prototype]]: Object

	1.  sayHello: ƒ () //ВОТ!!!!! До этого его тут небыло
	2.  constructor: ƒ Object()
	3.  hasOwnProperty: ƒ hasOwnProperty()
	4.  isPrototypeOf: ƒ isPrototypeOf()
	5.  propertyIsEnumerable: ƒ propertyIsEnumerable()
	6.  toLocaleString: ƒ toLocaleString()
	7.  toString: ƒ toString()
	8.  valueOf: ƒ valueOf()
	9.  __defineGetter__: ƒ __defineGetter__()
	10.  __defineSetter__: ƒ __defineSetter__()
	11.  __lookupGetter__: ƒ __lookupGetter__()
	12.  __lookupSetter__: ƒ __lookupSetter__()
	13.  __proto__: (...)
	14.  get __proto__: ƒ __proto__()
	15.  set __proto__: ƒ __proto__()

		1.  length: 1
		2.  name: "set __proto__"
		3.  arguments: (...)
		4.  caller: (...)
		5.  [[Prototype]]: ƒ ()
		6.  [[Scopes]]: Scopes[0] 
```

Для понимания сделаем новый пустой объект на основе person. 
```javascript
const lena = Object.create(person)

// И теперь выведем объект lena
// Объект lena унаследовал name а так же унаследовал прототип объекта person
// а так же прототип peroson (можно сказать объект Object)
1.  {}
1.  [[Prototype]]: Object
	1.  name: "Max"
	2.  [[Prototype]]: Object
		1.  sayHello: ƒ ()
		2.  constructor: ƒ Object()
		3.  hasOwnProperty: ƒ hasOwnProperty()
		4.  isPrototypeOf: ƒ isPrototypeOf()
		5.  propertyIsEnumerable: ƒ propertyIsEnumerable()
		6.  toLocaleString: ƒ toLocaleString()
		7.  toString: ƒ toString()
		8.  valueOf: ƒ valueOf()
		9.  __defineGetter__: ƒ __defineGetter__()
		10.  __defineSetter__: ƒ __defineSetter__()
		11.  __lookupGetter__: ƒ __lookupGetter__()
		12.  __lookupSetter__: ƒ __lookupSetter__()
		13.  __proto__: (...)
		14.  get __proto__: ƒ __proto__()
		15.  set __proto__: ƒ __proto__()

// Мы можем добавить поле name для объекта lena
lena.name = 'Elena'

//Сделаем вывод в консоль
// Теперь при lena.name будет выводтся Elena а не Max
1.  {name: 'Elena'}
	1.  name: "Elena"
	2.  [[Prototype]]: Object
		1.  name: "Max"
		2.  [[Prototype]]: Object
			1.  sayHello: ƒ ()
			2.  constructor: ƒ Object()
			3.  hasOwnProperty: ƒ hasOwnProperty()
			// И т.д.
```

И так как в JS всё является объектом - то теперь метод sayHello есть даже у строк. Так как строки это экземпляры String, а он наследуется от  Object. 
```javascript
const a = new String('Hello')

a.sayHello() // Hello

//Посмотрим на переменную а
1.  String {'Hello'}
	1.  0: "H"
	2.  1: "e"
	3.  2: "l"
	4.  3: "l"
	5.  4: "o"
	6.  length: 5
	7.  [[Prototype]]: String
	// Тут дальше методы String и prototype Object и в нём sayHello
	9.  [[PrimitiveValue]]: "Hello"

```

## Пример 
[[JS Context (this, call, bind, apply)#Пример с использованием this и prototype]]