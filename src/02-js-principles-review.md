# JavaScript Principles Review

## Executing JavaScript Code: A Review

```js
const num = 3;
const multiplyBy2 = (inputNumber) => {
    const result = inputNumber * 2;
    return result;
}
const name = "Will";
```

Code is saved (defined) in functions - but be run later.

AS soon as we start running our code, we create a _global execution context_.

* Thread of exectuion (parsing and executing the code line after line)
* Live memory of variables with data  (known as Global Variable Environment)

This is not the same as defining a function. When you execute a function you create a new execution context comprising:

1. The thread of exection (we go through the code **in the function** line by line).
2. A local memory ('Variable environment') where anything defined in the function is stored.

## Call Stack Review

The call stack is where code is pushed to and popped from in order to be ran.

![call-stack](/img/02-call-stack.png)

## Functions Review

Suppose we have a function copyArracyAndMultiplyBy2. Let's diagram it out.

```js
const copyArrayAndMultiplyBy2 = (array) => {
    const output = [];
    for(let i = 0; i < array.length; i++) {
        output.push(array[i] * 2);
    }
    return output;
}

const myArray = [1, 2, 3];
const result = copyArrayAndMultiplyBy2(myArray);
```

What if we want to copy array and divide by 2?

```js
const copyArrayAndDivideBy2 = (array) => {
    const output = [];
    for(let i = 0; i < array.length; i++) {
        output.push(array[i] / 2);
    }
    return output;
}

const myArray = [1,2,3]
const result = copyArrayAndDividBy2(myArray);
```

The problem we have here is lots of duplicate code with very little change.
