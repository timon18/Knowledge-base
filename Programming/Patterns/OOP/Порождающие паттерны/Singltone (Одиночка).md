06-04-2022
17:16
Authors: Khutuev Tamerlan, Eloev Georgiy.
***
Tags: #oop #patterns 
***
# Одиночка

Паттерн Singleton — это порождающий шаблон, который гарантирует, что класс имеет только один экземпляр, и обеспечивает глобальную точку доступа к этому экземпляру. Этот шаблон часто используется, когда требуется один экземпляр класса для координации действий в системе, таких как подключение к базе данных, служба ведения журналов или диспетчер конфигурации.

>**Одиночка** — это порождающий паттерн проектирования, который гарантирует, что у класса есть только один экземпляр, и предоставляет к нему глобальную точку доступа.
>(https://refactoring.guru/ru/design-patterns/singleton)

>Гарантирует, что у класса существует только один экземпляр, и предоставляет к нему глобальную точку доступа.
>(Паттерны объектно-ориентированного программирования 2020. GoF)


## Проблема
Паттерн Singleton используется, когда требуется, чтобы у класса был только один экземпляр и к нему можно было обращаться из разных частей программы.

>Для некоторых классов важно, чтобы существовал только один экземпляр. В системе может быть много принтеров, но может существовать лишь один спулер. В операционной системе должна быть только одна файловая система и единственный оконный менеджер. В цифровом фильтре может находить- ся только один аналого-цифровой преобразователь (АЦП). Бухгалтерская система обслуживает только одну компанию
>(Паттерны объектно-ориентированного программирования 2020. GoF)


## Решение
Паттерн Singleton решает эту проблему, предполагаемый метод getInstance(), который создает экземпляр объекта, если он еще не был создан, и возвращает этот экземпляр в любом случае. Таким образом, гарантируется, что у класса всегда будет только один экземпляр.

## Пример

Если есть необходимость что бы у класса был только один инстанс. 
Можно использовать например для подключения к базе данных. 

```javascript
class Database {
	constructor(data){
		// Если конструктор уже 1 раз вызывался
		if(Database.exist) {
			return Database.instance // Вернуть прошлый инстанс
		}
		// Возможно записывает в proto
		Database.instance = this // При вызове конструтора присвоится инстанс
		Database.exist = true // При вызове конструктора поле станет true
		this.data = data
	}
	getData() {
		return this.data
	}
}

const mongo = new Database('MongoDB')
console.log(mongo.getData())
// MongoDB


cosnt mysql = new Database('MySQL')
console.log(mysql.getData())
//Будет опять MongoDB
