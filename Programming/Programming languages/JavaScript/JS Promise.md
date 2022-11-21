04-04-2022
13:05
***
Tags: #javascript 
***
# JS Promise
Если простыми словами - promise это объект который содержит одно из своих состояний: 
- `pending` («ожидание»)
- `fulfilled` («выполнено успешно») 
- `rejected` («выполнено с ошибкой»)

Для создания используется следующий синтаксис:
```javascript
// Принимает 2 параметра (функции)
const p = new Promise((resolve, reject) => {
	// Ассинхронный код который мы хотим выполнить
	// Конечно можно и синхронный.... но не имеет смысла

	//Далее тут можно вызвать resolve или reject
	//Если всё нормально -> resolve
	//Если ошибка -> reject
})

p.then((data)=>{
	//Выполнится этот кода если был вызван resolve
	//при выполнеии промис может предавать данные 
	//в примере data
}
).catch((error)=>{
	//Выполнится этот кода если был вызван reject
	//При reject промис может передавать ошибку
}
).finally(()=>{
	//Выполнится всегда в конце
})
```
Но для чего они нужны? К примеру нам нужно сделать всякие ассинхроныне операции один за другим. Это можно сделать с помощью коллбек функций. Будем использовать setTimeout для наглядности. 
```javascript
console.log("Req data...")

setTimeout(() => {
	console.log('Preparing data...')
	setTimeout(() => {
		console.log('Data recived')
	}, 2000)
},2000)

//Req data...
//Preparing data...
//Data recived
```
Но есть небольшие проблемы. Одна из них это слишком большая вложенность. (называют адом коллбеков)

Теперь сделаем то же самое на промисах. Теперь нет вложенности и легче ловить ошибки. 
```javascript
console.log("Req data...")

const p = new Promise((resolve, reject) => {
	setTimeout(() => {
	console.log('Preparing data...')})
	const data = "Data"
	resolve(data)
	if('ERROR'){ // Если бы была ошибка к примеру
		const error = "error"
		reject(error)
	}
})

p.then((data) => {
	console.log('Data recived', data)
})
.then((data) => { // Изменим data
	data.modify = true
	return data
})
.catch((error) => {
	console.log('Error', error)
})
.finally(()=>{
	console.log('Finally')
})
```