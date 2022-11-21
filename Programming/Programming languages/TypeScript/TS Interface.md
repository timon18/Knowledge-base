04-04-2022
15:13
Authors: Khutuev Tamerlan.
***
Tags: #typesript 
***
# Interface TS
Интерфейс - это способ определения типа объекта.

Похожи на type но есть отличия -> [[TS Type aliases#Отличия от interface]]

```typescript
interface Point {
	x: number;
	y: number;
}

function printCoords(pt: Point) { 
	console.log(`Значение координаты 'x': ${pt.x}`) 
	console.log(`Значение координаты 'y': ${pt.y}`) 
}

printCoords({x:3, y:7})
```

Интерфейсы можно расширять, добавлять новые поля и удалять их. 

---
#### Расширение интерфейса
```typescript
interface IUser{
	id: number;
	name: stting;
}

interface IUser{
	age: number;
}
// Теперь в интерфейсе 3 поля
```

---
#### Наследование интерфейса
```typescript
interface IPerson{
	name: string;
	age: number;
}

interface IStuff extends IPerson{
	job: string;
}
//теперь IStuff имеет все поля IPerson
```

---
Если у нас есть объект в котором могут быть куча разных полей (к примеру css стили), то мы может так указать:
```typescript
interface Styles {
	[key: string]: string
}

//И потом 
const css: Styles {
	border: '1px'
	marginTop: '2px'
	// И т.д
}
```