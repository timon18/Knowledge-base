04-04-2022
15:08
***
Tags: #typesript 
***
# Функции TS
При объявлении функции можно указать каких типов параметры она принимает, а так же тип который она возвращает. 
```typescript
//В данном примере функция принимает и возвращает string
function sayHello(name: string): string {
	return `Hello, ${name}`
}
```

Типы объектов можно определять напрямую или через интерфейсы. 
[[TS Interface]]
```typescript
function printCoords(pt: { x: number, y: number }) { 
	console.log(`Значение координаты 'x': ${pt.x}`) 
	console.log(`Значение координаты 'y': ${pt.y}`) 
} 

printCoords({ x: 3, y: 7 })
```

Можно так же делать перегрузку функций -> [[TS Перегрузка функций]]