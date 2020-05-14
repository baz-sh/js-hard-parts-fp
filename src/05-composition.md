# Composition

## Function Composition

**JavaScript the Hard Parts - Functional Programming.**

1. Principles of JavaScript
2. Higher order functions
3. Arrow and anonymous functions
4. `reduce, filter` and chaining higher order functions
5. **Function composition & pure functions**
6. Closure
7. Function decoration
8. Partial application and currying

**Function composition.**

- Chaining with dots relies on JavaScript prototype feature-functions return arrays which have access to all the HOFs (map, filter, reduce)
- I'm passing my output into the next function automatically
- What if I want to chain functions that just return a regular output
- e.g. `multiplyBy2, add3, divideBy5`

**We could keep track of things with global variables.**

```js
const multiplyBy2 = x => x*2
const add3 = x => x+3
const divideBy5 = x => x/5

const initialResult = multiplyBy2(11)
const nextStep = add3(initialResult)
const finalStep = divideBy5(nextStep)

console.log("finalStep", finalStep)
```

But this is risky, people can overwrite.

**We can use the face that JS evaluates every function call before it moves on.**

```js
const multiplyBy2 = x => x*2
const add3 = x => x+3
const divideBy5 = x => x/5

const result = divideBy5(add3(multipleBy2(11)))
```

Now this is pretty unreadable though ☹️

_(Btw this relies on our function being 'referentially transparent'-we can replace the call to the function with its return value with no consequences on our app)._

**Reduce as _the_ most versatile function in programming.**

```js
const multiplyBy2 = x => x*2
const add3 = x => x+3
const divideBy5 = x => x/5

const reduce = (array, howToCombine, buildingUp) => {
    for (let i = 0; i < array.length; i++) {
        buildingUp = howToCombine(buildingUp, array[i])
    }
    return buildingUp
}

const runFunctionOnInput = (input, fn) => {
    return fn(input)
}

const output = reduce([multiplyBy2, add3, divideBy5], runFunctionOnInput, 11)
```

## Function Composition with Reduce

![reduce-1](/img/05-reduce-1.png)

![reduce-2](/img/05-reduce-2.png)

As you can see following this through, reduce is incredibly powerful and the essence of functional programming.
