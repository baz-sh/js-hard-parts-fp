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

**Calling a function inside the function call in which it was defined.**

```js
const outer = () => {
    let counter = 0;
    const incrementCounter = () => {
        counter++;
    }
    incrementCounter();
}

outer();

incrementCounter();     // ERROR, can't do this.
```

What determines what data your function have access to when you call the function? Where we call it?

![inner-function](/img/07-inner.png)

**There is a way to run a function outside where it was defined.**

Without an error - we return the inner function and assign it to a new global label.

```js
const outer = () => {
    let counter = 0;
    const incrementCounter = () => {
        counter++;
    }
    return incrementCounter
}

const newFunction = outer();
newFunction();
newFunction();
```

**Now we can call the function that was originally saved as `incrementCounter` by its new global label, `newFunction`...

But we have a problem 😭

## Outer Function

`newFunction` has a private property  which is `counter`. This can only be referenced by `incrementCounter` now known as `newFunction`. It is hidden and protected.

When `outer` ran on the call stack and `incrementCounter` was saved, it immediately got a link to the surrounding memory. Which included `counter`.

When we run `newFunction` it looks in it's local memory for counter, which it doesn't find. It goes to it's definition and looks into its hidden `scope` property aka `the backpack` and finds it.

![closure-2](/img/07-closure-outer.png)

## Closure Clarifications & Review

There are various names for the `back pack` or hidden `scope` property. They are:

* Persistant lexically scoped reference data (🤓)
* Variable environment
* Closed over variable environment

Each of these are referred to by Will as `the back pack`.

In practice, these are all known as _*Closure*_.
