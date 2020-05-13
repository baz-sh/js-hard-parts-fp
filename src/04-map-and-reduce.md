# Map & Reduce

## Map

Developers tend to call copyArrayAndManipulate, map

```js
const map = (array, instructions) => {
    const output = [];
    for(let i = 0; i < array.length; i++) {
        output.push(instructions(array[i]))
    }
    return output;
}

const multiplyBy2 = input => input * 2;
const result = map([1,2,3], multilpyBy2);
```

## Reduce Intro

Reduce and reducers

* _The_ most versatile higher order function of all
* Takes a mental shift to look at problems through the reduce lens
* Can even enable function composition (to come)

### We have alread sen 'reduction' in action

```js
const map = (array, instructions) => {
    const output = [];
    for(let i = 0; i < array.length; i++) {
        output.push(instructions(array[i]))
    }
    return output;
}

const multiplyBy2 = input => input * 2;
const result = map([1,2,3], multilpyBy2);
```

What is  map actually doing? (accumulator, push etc)

What's happening in the mapping is taking the first element, doubling it and then combining it by pushing it into an empty array. This is reducing it from two things (first element and array) into one thing, array with a value.

When you take an array and a number, that's two things. You can reduce it to one thing by doubling it and pushing the element.

![reduce](/img/04-map-reduce.png)

How else could we 'combine and use, combine and use'?

* Take the number 0 and comine with array[0] by adding, take that combined value and combine with array[1] by addint and so forth...
* Take the empty string "" and combine with array[0] by appending, take that combined value and comine with array[1] by appending and so forth...

We'd want to write our function so that it could handle:

* Any 'accumulator' (array, string, number)
* Any combining logic/code/functionality (the 'reducer')

## Reduce Example

This function is known as `reduce` - it can handle a remarkable range of tasks

```js
const reduce = (array, howToCombine, buildingUp) => {
    for (let i = 0; i < array.length; i++) {
        buildingUp = howToCombine(buildingUp, array[i])
    }
    return buildingUp
}

const add = (a, b) => a + b
const summed = reduce([1,2,3], add, 0)
```

Should be called 'reduce from 2 things to 1 repeatedly, inside'.

![reducer](/img/04-reducer.png)

Reduced diagrammed in full

![reducer-full](/img/04-reducer-full.png)

## Built-in Array Methods

Interlude - arrays, objects and functions have access to 'methods'

* 'methods' are functions that they can use on themselves

```js
const array = [1,2,3]
array.push(10) // Where's this push method come from?
```

* The 'methods' that arrays get are stored in an object that every array has access to when you refer to the array, followed by a 'dot' and the method name (See OOP JS Hard Parts)
* The link to this object full of shared methods is on the `__proto__` property.

### JavaScript has a built-in version of reduce available to all arrays

Reminder of our version of reduce

```js
const add = (a,b) => a+b
const summed = reduce([1,2,3], add, 0) // summed is 6
```

With the build-in version, the array is inserted into the `reduce` function automatically as the first input/argument. But they produce the same result.

```js
const add = (a,b) => a+b
const summed = [1,2,3].reduce(add,0) //summed is 6
```

## Filter

### In fact we get a number of build-in higher order functions in JavaScript

* map, forEach, filter, flatMap, reduce, reduceRight
* All 'iterate' through each element of the array and run a function on each
* But behave differently - MDN guides us

```js
const array = [1,2,3,4,5,6]
const greaterThan2 = num => num > 3

const filteredArray = array.filter(greaterThan2) // [3,4,5,6]
```

## Chaining Array Methods

