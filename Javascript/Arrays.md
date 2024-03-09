```javascript
let a = [1, 2, 3, 4]

// traditional way of printing items in a list
for (let i = 0; i < a.lenth; i++) {
	console.log(`${i}`);
}

// cleaner way of doing it, provides indexes
for (const i in a) {
	console.log(`a[${i}] = ${a[i]}`);
}

// if  dont care about the index and just wanna print the values use
for (const i of a) {
	console.log(`${i}`);
}

// const note: even though a list or object is a const, its members can still be changed
```

## Manipulating arrays

```js
let numbers = [2, 3, 4, 5];
let doubled = numbers.map((number) => number * 2); // apply to every element in array
let filtered = numbers.filter(age => age > 10); // return filtered amount of array
let sum = numbers.reduce((acc, item) => acc + item); 

```