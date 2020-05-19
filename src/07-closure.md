# Closure

Closure acts as a superpower.

**Closure**.

* The most esoteric concept in JavaScript
* Functions are our units to build with but they're limited-they forget everything each time they finish running-with no global state
* Imagine if we could give our functions memories

**Reminding ourselves of how functions actually work**.

```js
const multiplyBy2 = inputNumber => inputNumber*2;

const output = multiplyBy2(7);
const newOutput = multiplyBy2(3);
```

No memory of the previous execution-imagine if we could give our functions permanent memories.

It begins with returning a function from a function.

**Let's run a our generated function with the input 3**.

```js
const functionCreator = () => {
    let counter = 0;
    const add3 = (num) => {
        const result = num+3
        return result
    }
    return add3
}

const generatedFunc = functionCreator();
const result = generatedFunc(2) //5
```

## Closure Under the Hood

![closure](/img/07-closure.png)

## Closure Clarifications

All arrays objects and functions end up on the heap with regards to their memory. Global memory might 'point' to an address here to reference something.

## Inner Function



## Outer Function



## Closure Clarifications & Review


