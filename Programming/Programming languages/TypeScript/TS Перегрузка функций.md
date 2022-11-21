04-04-2022
16:02
***
Tags: #typesript 
***
# Перегрузка функций в TS
```typescript
interface MyPosition {
	x: number | undefined
	y: number | undefined
}

interface MyPositionWithDefault extends MyPosition {
	default: string
}

function position(): MyPosition
function position(a: number): MyPositionWithDefault
function position(a: number, b:number): MyPosition

function position(a?: number, b?: number){
	if(!a && !b){
		return {x: undefined, y: undefined}
	}

	if(a && !b) {
		return {x: a, y: undefined, default: a.toString()}
	}

	return {x: a, y: b}
}

console.log(position()) // {x: undefined, y: undefined}
console.log(position(42)) // {x: 42, y: undefined, default: '42'}
console.log(position(42, 15))// {x: 10, y: 15}
```


