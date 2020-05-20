# Function Decoration & Partial Application

## Function Decoration Introduction

* Now we can convert functions more easily to make them suit our task
* Without writing a new function from scratch
* We can run code _on other bits of code_ to appear to change them

**To add a permanent memory to an existing function we have to create a new function that will run the existing function inside of itself**.

```js
const oncify = (convertMe) => {
    let counter = 0;
    const inner = (input) => {
        if (counter === 0) {
            const output = convertMe(input);
            counter++;
            return output;
        }
        return "Sorry"
    }
    return inner;
}

const multiplyBy2 = num => num*2;
const oncifiedMultiplyBy2 = oncify(multiplyBy2)

oncifiedMultiplyBy2(10)     // 20
oncifiedMultiplyBy(7)       // Sorry
```

## Decorating a Function

![function-decoration](/img/08-function-decoration-1.png)

## Invoking a Decorated Function

![function-decoration-invokation](/img/08-function-decoration-2.png)

## Function Decoration Review

* **Easier to add features-** We can 'pseudo' edit our function that we've already made - into functions that behave similar but with bonus features!
* **Easier to debug-** Definitely need to know how it's working under the hood!

## Partial Application Introduction

**Function composition is powerful but every function needs to behave the same way.**

* Taking in one input and returning out one output
* What if I have a function I want to use that expected two inputs
  * This is 'arity mismatch'
* We need to 'decorate' our function to prefill _one_ of its inputs

This means creating a new function that calls our multi-argument function - with the argument and the multi-argument function stored conveniently in the backpack.

## Partial Application Example

**This is known as 'Partial application'**.

```js
const mutliply = (a,b) => a*b;
function prefillFunction (fn, prefilledValue) {
    const inner = (liveInput) => {
        const output = fn(liveInput, prefilledValue);
        return output;
    }
    return inner;
}

const multiplyBy2 = prefillFunction(multiply, 2);
const result = multiplyBy2(5);
```

## Partial Application Clarifications

![partial-application](/img/08-partial-applicatiopn.png)

This is closure in functional programming style.

## Partial Application Review

**Partial application and currying.**

* In practice we may have to prefill one, two... multiple arguments at different times
* We can convert ('decorate') any function to a function that will accept arguments one by one and only run the function in full once it has all the arguments
* This is a more general version of partial application
* **Easier to add features-** Mismatched arity- no problem! We weite a function multiply _once_ and then reuse it for different situations by 'editing' its arguments
* **More readable-** We can use our composition/reduce to list out functions to run one-by-one on our data, even if the function expected more than 1 input!
* **Easier to debug-** Individual units of functionlity possible even with 1+ input expected

**Functional programming**.

Every line of code is named (or if not, is so short we can see exactly what it does), is an independent unit that has all of its consequences in that single line.

We can then couple up (compose) these sungle units of code/instructions (functions) up into complex tasks.

But with every  component of the task independent, recognizable, reusable, cersatile and easily debuggable!

**We have to do some feats to wrestle our tiny units of code (functions)**.

Combining up functions with multiple inputs from libraries.

We've seen many of them (higher order functions, reduction/composition, closure, function decoration, partial applcation and currying). And there are even more - monads, applicators et al!

**Readable, debuggable and easy to add features**.

```js
pipe(
    getPlayerName,
    getFirstName,
    properCase,
    addUserLabel,
    createUserTemplate
)([{name: 'will sentance', score:3}]);
```

But our code is now a set of independent, self contained steeps we can wield to solve any problem and become true composers of our code.
