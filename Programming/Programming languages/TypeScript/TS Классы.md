04-04-2022
16:24
***
Tags: #typesript 
***
# Классы TS
Классы в TS в основном идентичны классам из обычного JS.
Классы в JS -> [[JS Классы]]

```typescript

//Разница только в типах
class Typescript {
	version: string

	constructor(varsion: string) {
		this.version = version
	}

	info(name: string) {
		return `[${name}]: Typestring version is ${this.version}`
	}
}

class Car {
	//readonly можно изменять только в конструкторе
	readonly numberOfWeels: number = 5
	//readonly model: string
	//constructor(theModel){
		//this.model = theModel
	//}

	//Два вида добавления полей

	constructor(readonly model: string) {}
}
```

### Модификаторы полей
По умолчанию все поля класса public

#### Protected
Поля protected доступны в самом классе, а так же во всех классах которые наследуются от него. Но у через экземпляр класса нельзя получить доступ к полю или методу. 

#### Public
Доступны везде. По умолчанию. 

#### Private
Поля private доступны только в том классе где объявлены. 