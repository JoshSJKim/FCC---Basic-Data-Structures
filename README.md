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
      two: 2
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

Or, this works as well

```js
const arr = [2, 4, 5, 1, 7, 5, 2, 1];
arr.shift();        // remove the first element first
arr.splice(3, 4);   // based on the remaining array elements, remove 4 elements beginning at index[3]
console.log(arr;)   // [4, 5, 1]
```

## Add Items Using splice()

- splice() method could actually take up to three parameters.
- First two are the same.
  - first, to indicate the start index
  - second, to indicate the number of elements to delete from the start index.
- The third parameter (could be comprised of multiple elements) is used to add items in place of the elements that were removed.

- There are a number of ways to go about this
- You could initialize variables to pass to the parameters

```js
const numbers = [10, 11, 12, 12, 15];   // nonsense sequence of numbers
const startIndex = 3;                   // indicate which element to start, the second 12
const amountToDelete = 1;               // delete 1 element, which is the indicated element itself

numbers.splice(startIndex, amountToDelete, 13, 14); // start at index 3 (12), delete 1 element (12), and add in 13 and 14 it its place
console.log(numbers);   // [10, 11, 12, 13, 14, 15] A sensible sequence of numbers
```

Or go directly to the array.

### Exercise (add using splice)

Remove first two color names from the array and add in 'DarkSalmon' and 'BlanchedAlmond' in its place

```js
function htmlColorNames(arr) {
  arr.splice(0, 2, 'DarkSalmon', 'BlanchedAlmond');
  return arr;
}

console.log(htmlColorNames(['DarkGoldenRod', 'WhiteSmoke', 'LavenderBlush', 'PaleTurquoise', 'FireBrick']));
```

- Console will display ['DarkSalmon', 'BlanchedAlmond', 'LavenderBlush', 'PaleTurquoise', 'FireBrick']

## Copy Array Items Using slice()

- slice() - not splice() - is a method used to copy or extract defined number of elements into a new array.
- The original array which is called upon is not modified at all.
- slice() takes two parameters
  - first parameter defines the index at which the extraction begins
  - second parameter defines the index at which the extraction stops
- NOTE: Extraction will occur up to, but not include the element at the index at which extraction stops.

```js
let weatherConditions = ['rain', 'snow', 'sleet', 'hail', 'clear'];
let todaysWeather = weatherConditions.slice(1, 3);
console.log(todaysWeather);   // ['snow', 'sleet']
console.log(weatherConditions); // ['rain', 'snow', 'sleet', 'hail', 'clear']
```

### Exercise (copy using slice)

- extract 'warm' and 'sunny' and assign it to a new array

```js
let weatherConditions = ['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms'] // weather conditions object is declared globally with its array
function forecast(arr) {
  let todaysForecast = arr.slice(2, 4); // slice method to extract 'warm' and 'sunny' from the array passed to the function
  console.log(todaysForecast);    // console.log method to check if the return value is indeed the result expected. block scope. It will not show outside the function
  return todaysForecast;
}

console.log(forecast(weatherConditions)); // console will display ['warm', 'sunny'] as a result of returning the result of the 'forecast' function globally
console.log(weatherConditions);  // The original array is not modified ['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']
```

## Spread Operator

### Copy an Array with spread operator

- While slice() method allows selective extraction, the use of spread operator allows you to copy an entire array and assign it to a new array.
  
```js
let thisArray = [true, true, undefined, false, null];
let thatArray = [...thisArray];   // (...) is the spread operator
console.log(thatArray);   // console will display the exact same array as 'thisArray'
```

#### Exercise (copy with spread operator)

- function 'copyMachine' will take an array and a number as its arguments
- The function is supposed to return a new array comprised of 'num' copies of the array

```js
function copyMachine(arr, num) {  // function copyMachine will take an array and a number value 'num' as its arguments
  let newArr = [];                // When function is called, a new array 'newArr' is created with an empty string
  while (num >= 1) {              // the condition: while 'num' value passed is greater than or equal to 1, execute the following
    let obj = [...arr];           // This part isn't really necessary, but it passes. Declare a variable 'obj' with the array 'arr' unpacked using spread operator
    newArr.push(obj);             // push declared 'obj' into new array 'newArr' while condition is true (newArr.push([...arr]); is viable as well)
    num--;                        // decrement 'num' value by 1 for every loop until num = 1.
  }
  return newArr;                  // return newArr
}
```

### Combine Arrays with the spread operator

- The spread operator also provides the ability to combine arrays (i.e. insert all the elements of one array into another, at any index)
- Traditional syntaxes also provides the ability to concatenate arrays, but it only allows combining arrays at the end, or beginning of another.

```js
let thisArray = ['sage', 'rosemary', 'parsley', 'thyme'];
let thatArray = ['basil', 'cilantro', ...thisArray, 'coriander'];
```

#### Exercise (combine with spread operator)

- function spreadOut should return the variable 'sentence'
- Modify the function using the spread operator so that it returns the array ['learning', 'to', 'code', 'is', 'fun']

```js
function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning', ...fragment, 'is', 'fun'];
  return sentence
}

console.log(spreadOut());  // ['learning', 'to', 'code', 'is', 'fun']
```

## Check for the Presence of an Element with indexOf()

- Arrays can be changed, or mutated, at any given time.
- There is no guarantee about where a specific data will be on a given array, or if that element even exists.
- Use indexOf() to check for the existence of the specified element in an array.
- indexOf() takes an element as its parameter.
- When called, it will return its index position in the array, or '-1' if the data does not exist.

```js
let fruits = ['apples', 'pears', 'oranges', 'peaches', 'pears'];

fruits.indexOf('dates');    // -1
fruits.indexOf('pears');    // 1 - It will return the first index at which the specified element is found
fruits.indexOf('apples');   // 0
```

### Exercise (indexOf())

- function quickCheck takes an array 'arr' and an element 'elem' as its arguments.
- Modify the function using indexOf() so that it returns 'true' if the passed element exists in the array and 'false' if it does not.

```js
function quickCheck(arr, elem) {
  if (arr.indexOf(elem) >= 0) {
    return true;
  } else {
    return false;
  }
}
```

- The above is more traditional syntax
- It can be simplified using the ternary condition

```js
function quickCheck(arr, elem) {
  return arr.indexOf(elem) >= 0 ? true : false;
}
```

- Another method is simply returning the comparison

```js
function quickCheck(arr, elem) {
  return arr.indexOf(elem) != -1;
}
```

## Iterate through Array's Items using for Loops

- It's very useful to be able to iterate through items in an array to find one or more elements as needed.
- Or to manipulate an array based on which data items meet certain sets of criteria.
- There are several built-in methods in JS to iterate through items in slightly different ways to achieve different results.
- For example every(), forEach(), map()
- But the most flexible method that provides the greates control is the simpel 'for' loop.

```js
function greaterThanTen(arr) {
  let newArr = [];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] > 10) {
      newArr.push(arr[i]);
    }
  }
  return newArr;
}

console.log(greaterThanTen([2, 12, 8, 14, 80, 0, 1]));    // [12, 14, 80]
```

- The simple function shown above will iterate through an array passed to the function as its argument and it will push elements that have values greater than 10 to newly declared array 'newArr'.

### Exercise (for loop iteration)

- function 'filteredArray' takes nested array 'arr' and element 'elem' as its arguments, and it will return a new array
- 'elem' represents an element that may or may not exist in the nested array passed.
- Modify the function using a for loop
  - to return a filtered version of the array such that any array nested within 'arr' containing 'elem' is removed.

```js
function filteredArray(arr, elem) {
  let newArr = [];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i].indexOf(elem) == -1) {   // This will iterate through the subarrays and look for 'elem'. 
      newArr.push(arr[i]);              // If specified 'elem' is not found in the subarray, push that subarray into 'newArr'
    }
  }
  return newArr;
}
```

## Create Complex Multi-dimensional Arrays

- Multi-dimensional arrays, or nested arrays, can become quite complex

```js
let nestedArray = [
  ['deep'],                     // 2 levels
  [
    ['deeper'], ['deeper']      // 3 levels
  ],
  [
    [
      ['deepest'], ['deepest']  // 4 levels
    ],
    [
      [
        ['deepest-est?']        // 5 levels
      ]
    ]
  ]
];
```

- It is very common to create complex arrays, especially when dealing with large amounts of data.
- No matter how complex, it is still quite easy to access complex arrays with bracket notation

```js
console.log(nestedArray[2][1][0][0][0]); // 'deepest-est?'
```

- The above element can be reassigned with a new value

```js
nestedArray[2][1][0][0][0] = 'deeper still';
```

