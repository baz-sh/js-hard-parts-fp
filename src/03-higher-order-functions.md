# Higher Order Functions

## The Problem: Repetitive Functions

In our code so far, we have iterated over an item in an array and done something _different_. Other than that the code is the same.

![image](/img/03-repeat.png)

## Generalizing Functions

We could generalize our function so that we pass in our specific instruction only when we run the copyArrayAndManipulate function!

```js
const copyArrayAndManipulte = (array, instructions) => {
    const output = [];
    for(let i = 0; i < array.length; i++) {
        output.push(instructions(array[i]));
    }
    return output;
}

const multiplyBy2 = (input) => {
    return input * 2;
}

const result = copyArrayAndManipulate([1,2,3], multiplyBy2);
```

## Higher-Order Functions Review

How was this possible?

> Functions in JavaScript = first class objects

They can co-exist with an can be treated like any other javascript object

1. assigned to variables and porperties of other objects
2. passed as arguments into functions
3. returned as values from functions

Higher order functions

* **Easier to add features**- we don't need to build a brand new `copyArrayAndAdd3` function- just use `copyArrayManipulate` with the input of `add3`. Higher order functions keep our code DRY
* **More readable**- `copyArrayManupulate(multiplyBy2)`- I know what this is doing more readily than the for loop style
* **Easier to debug**- as long as we understand what's happening under-the-hood

## Arrow & Anonymous Functions

Arrow functions in ES2015

```js
const multiplyBy2 = (input) => { return input*2 };
```

So where the function is a single expression to evaluate and then return, ES2015 lets us remove the `{}` and return keyword.

```js
const multiplyBy2 = (input) => input*2
const output = multiplyBy2(3) // 6
```
