04-04-2022
15:30
Authors: Khutuev Tamerlan.
***
Tags: #stub 
***
# Type aliases
Их ещё называют синонимами типов. 
Их можно использовать если мы хотим использовать один и тот же тип в некоторых местах. 
Они похожи на интерфейсы [[TS Interface]]. 

####  Отличия от interface
Но в отличии от интерфейсов на основе type нельзя создавать другие типы или как то расширять или изменять их. В остальном они похожи. 

```typescript
type login = string

// Переменная должна бать одним из типов
type ID = number | string

type Point = { 
	x: number;
	y: number;
}

printCoords(pt: Point) { 
	console.log(`Значение координаты 'x': ${pt.x}`) 
	console.log(`Значение координаты 'y': ${pt.y}`) 
} 
printCoords({ x: 3, y: 7 })
```

Type не может быть изменён после создания.
```typescript
type Window = { 
	title: string 
} 
type Window = { 
	ts: TypeScriptAPI 
} 
// Ошибка: повторяющийся идентификатор 'Window'.
```