# Purity & Immutability

## Pure Functions

* Functions as tiny units to be combined and run automatically **must** be highly predictable.
* We rely on using their evaluated result to pass the input to the next unit of code (automatically). Any 'side effects' would destroy this.

```js
let num = 10

const add3 = x => {
    num++
    return x+3
}

add3(7)
```

This isn't a pure function. It's mutating `num`.

## Immutability

```js
const array = [1,2,3]
const multiplyBy2 = num => num*2

const result = array.map(multiplyBy2)       // [2,4,6]
const newResult = array.map(nultiplyBy2)    // [2,4,6]
```

If we want the only consequence of map to be on that line and to achieve 'referential transparency' (I can replace the function acll with its output and it's the same) - then I need to preserve my data and not manipulate it.

JavaScript passes a reference ('link back') to the `arr` when it's intserted into the function `map`. If we change ('mutate') the input array our function is not pure = it's unpredictable - I can't figure out what it does just by reading it and looking at its output there in that line - this undoes all our hard work.
