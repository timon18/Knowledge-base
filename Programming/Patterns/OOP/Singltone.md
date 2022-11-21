c06-04-2022
17:16
***
Tags: #oop #pattern 
***
# Singltone
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
