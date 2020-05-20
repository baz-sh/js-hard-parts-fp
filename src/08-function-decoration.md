# Function Decoration & Partial Application

## Function Decoration Introduction

* Now we can convert functions more easily to make them suit our task
* Without writing a new function from scratch
* We can run code _on other bits of code_ to appear to change them

**To add a permanent memory to an existing function we have to create a new function that will run the existing function inside of itself**.

```js
const oncify = (convertme) => {
    let counter = 0;
    const inner = (input) => {
        if (counter === 0) {
            const output = converMe(input);
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

## Function Decoration Review

## Partial Application Introduction

## Partial Application Clarifications

## Partial Application Review
