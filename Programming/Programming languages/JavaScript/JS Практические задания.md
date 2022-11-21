30-11-2021
12:11
Authors: Khutuev Tamerlan.
***
Tags: #programming #javascript 
***
# Практические задания по JS


## Вернуть количество элементов в массиве
```js
const arr1 = [1, 2, 3, 4, 5]
const getElementCount = (arr) => {
	let count = 0;
	for (let i of arr) {
		count++;
	}
	return count;
}
console.log(getElementCount(arr1)) //5
```

---

## Вывод всех элементов соответствующих значению/условию в массиве
```js
onst arr1 = [1, 2, 3, 4, 5]

const getElement = (arr, a) => {
	let arr2 = [];
	
	for (let i of arr) {
		if (i === a) {
			arr2.push(i)
		};
	};
	
	return arr2;
}

console.log(getElementCount(arr1, 5)); // [5]
```
Вопрос. Как лучше писать? 
```js
if (i === a) {
	arr.push(i);
}

//or

if (i === a) arr.push(i);
```

---

## Вывести количество элементов соответствующих условию
```js
const TestFunc = (arr, a) => {
	let counter = 0;
	
	for (let i of arr) {
		if (i === a) counter++;
	};
	
	return counter;
};

```

---

## Вывести индекс элемента в массиве
```js
const getElementIndex = (arr, a) => {
	indexArr = [];
	arr.forEach((item, index) => {
		if (item === a) indexArr.push(index);
});

return indexArr;
```

---

## Найти индекс последнего элемента в массиве, который соответсвует значению
```js
const testFunc = (arr, a) => {
	let lastIndex = null;
	arr.forEach((item, index) => {
		if (item === a) lastIndex = index;
	});
	return lastIndex;
}

```

---

## Вывод всех объектов соответствующих значению/условию в массиве объектов
```js
r = [
	{
	name: 'Anya',
	age: 45,
	},
	{
	name: 'Sanya',
	age: 83,
	},
	{
	name: 'Tanya',
	age: 25,
	},
];

const testFunc = (collection, key, value) => {
	let arr2 = [];
	
	collection.forEach(item => {
		if (item[key] === value) arr2.push(item);
	});
	return arr2;
}

console.log(testFunc(r, 'name', 'Tanya'))
```

---

## Вывод всех элементов, где совпадает хотя бы одно значение из массива
```js
const testFunc2 = (arr, val1, val2) => {
	let arr2 = []
	for(let i of arr) {
		if(i === val1 || i === val2) arr2.push(i)
	};
	return arr2;
}

console.log(testFunc2(q, 1, 5))
```

---

## Вывод всех объектов, где совпадает сразу несколько полей значений из массива объектов
```js
const testFunc = (collection, value1, value2) => {
	let arr2 = [];
	
	collection.forEach(item => {
		if (item.name === value1 && item.age === value2) {
			arr2.push(item)
		};
	});
	
	return arr2;
}
```

---

## Вернуть все элементы, которые противоположны предоставленному условию
```js
const testFunc = (collection, value1, value2) => {
	let arr2 = [];
	
	collection.forEach(item => {
		if (item.name === value1 && item.age === value2) {
			arr2.push(item)
		};
	});
	
	return arr2;
}
```

---

## Вернуть массив значений соответствующих ключу из массива объектов
```js
const testFunc = (collection, key) => {
	let arr2 = [];
	
	collection.forEach(item => {
		arr2.push(item[key]);
	});
	
	return arr2;
};

console.log(testFunc(r, 'name'))
```

---

## Найти максимальный/минимальный элемент в массиве и массиве объектов
```js
const testFunc = (collection, maxmin) => {
	let val = collection[0].age;
	collection.forEach(item => {
		if (maxmin === 'max') {
			if (item.age > val) val = item.age;
		} 
		
		else if (maxmin === 'min') {
			if (item.age < val) val = item.age;
		}
	});
	
	return val;
}
```

---

## В функцию подается несколько массивов. Вернуть один массив со всеми элементами. 
```js
const testFunc3 = (...arrs) => {
	let arr2 = [];
	for (let i of arrs) {
		arr2.push(...i);
	};

	return arr2;
};

//or

const testFunc3 = (...arrs) => {
	let arr2 = [];
	arrays.forEacj(array => {
		array.forEach(item => arr2.push(item));
	});

	return arr2;
};

```

---

## Напишите функцию moveElement(arr,from,to), которая позволяет поменять местами элементы из позиции from в позицию to. 
```js
const moveElemen = (arr, from, to) => {
	a = arr[to];
	arr[to] = arr[from];
	arr[from] = a;

	return arr;
}

t = [1, 2, 3, 4, 5]
console.log(moveElemen(t, 4, 0))
```

---

## 
```js
```

---