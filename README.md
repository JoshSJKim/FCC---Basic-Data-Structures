# FCC---Basic-Data-Structures

Arrays and Objects, its application, JS methods for data access and manipulation

## Use an Array to Store a Collection of Data

- Arrays can be used to store various data types at once.

```js
let simpleArray = ['one', 2, 'three', true, false, undefined, null];
console.log(simpleArray.length);    // 7
```

- A more complex array can be implemented as well.
- Complex arrays are also called multi-dimensional arrays, which consists of multiple levels of arrays nested in other arrays.
- Complex arrays can also contain objects.

```js
let complexArray = [
  [
    {
      one: 1,
      tow: 2
    },
    {
      three: 3,
      four: 4
    }
  ],
  [
    {
      a: "a",
      b: "b"
    },
    {
      c: "c",
      d: "d"
    }
  ]
];
```

## Access an Array's Contents Using Bracket Notation

- The fundamental feature of any data structure is the ability to store data, and also access and retrieve the stored data.

Shown below is a simple array

```js
let ourArray = ["a", "b", "c"];
```

- Each item/element in an array has an index, which serves as the position of that item in the array.
- Remember JavaScript uses zero-based indexing.
- Use bracket notation to access an item in an array as shown below.

```js
let ourVariable = ourArray[0];
```

- The above variable declaration will retrieve the item placed in the '0th' position in ourArray and assign it to 'ourVariable'

- Also, use the same notation to reassign a value to a specific position in the array.

```js
ourArray[1] = "not b anymore";
console.log(ourArray);      // Console will display ["a", "not b anymore", "c"]
```

## Add Items to an Array with push() and unshift()

- The length of an array is not fixed.
- Arrays can be defined with any number of elements.
- Elements can be added or removed over time.
- In other words, arrays are mutable.

```js
let twentyThree = 'XXIII';
let romanNumerals = ['XXI', 'XXII'];

romanNumerals.unshift('XIX', 'XX');
romanNumerals.push(twentyThree);
console.log(romanNumerals);   //['XIX', 'XX', 'XXI', 'XXII', 'XXIII']
```

- Notice that you can pass values directly to the array or define variables to pass.

## Remove Items from an Array with pop() and shift()

- ```pop()``` and ```shift()``` removes an element from an array.
- The difference between pop, shift and push, unshift is that pop and shift do not take parameter.
- Each method allows an array to be modified by a single element at a time. i.e first or last element of the array.

```js
function popShift(arr) {      // Declare function
  let popped = arr.pop();     // Remove last element from array
  let shifted = arr.shift();  // Remove first element from array
  return [shifted, popped];   // Return the removed elements
}

console.log(popShift(['challenge', 'is', 'not', 'complete']));    // ['challenge', 'complete']
```

## Remove Items Using Splice()

- Use splice() method to remove elements in the middle of an array.
- Remove single element, or a series of elements.

```array.splice(num1, num2);```

- The above splice syntax takes 2 parameters.
  - First parameter refers to the index, or the position of the element in the array.
  - The second parameter refers to the number of elements to remove.
  - Note that the second parameter includes the element located in the index position.

```js
let array = ['today', 'was', 'not', 'so', 'great'];
array.splice(2, 2);   // splice will remove 2 elements beginning at index '2', which are 'not' and 'so'
console.log(array);   // ['today', 'was', 'great']
```

- splice() method can also return the removed elements by assigning it to a new array variable.

```js
let array = ['I', 'am', 'feeling', 'really', 'happy'];
let newArray = array.splice(3, 2);
console.log(newArray);    // ['really', 'happy']
```

Another example.

- Use a combination of removal methods to remove elements from 'arr' so that it only contains elements that sum to the value of 10

```js
const arr = [2, 4, 5, 1, 7, 5, 2, 1];
arr.splice(4, 4);   // remove 4 elements beginning at 7
arr.shift();        // remove the first element
console.log(arr);   // [4, 5, 1]
```
