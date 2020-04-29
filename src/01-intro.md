# Introduction

Functional programming is an ever increasing popular paradigm for structuring complex code.

## Let's suppose we have a quick game we're building

Every line of code either saves data to memory (e.g. a user's score) or uses that data (e.g. increase that user's score)

But with 1000s   of lines of code - every libe if code can potentially use (and **depend**) on that data 🥴

High risk - every time I want to change any line, I have to consider whether it could affect other lunes (and when I miss something, I get bugs)

What's the answer?

## The answer has been _functions_

**Compartmentalise**-Reduce the potential impact of any give nline to maybe 10 other lines (inside the function)

**But** even within a 10 luine function, 'resoning' through what each line does is hard - & the code may still have affects outside the function (via global variables)

_functions as we know them, may not be enough!_.

## Imagine if we could structure our code into individual pieces where _almost every single line_ is self-contained

* The only thing any given line depends on are inputs (explicitly stated in that very line)
* The only consequences of the line would be its output (explicitly stated in that very line)
* _And_ each line could get a nice human-readable label for when we use it!

This could transform how we write code, debug it and read about others' code.

But how could we do it!? 😲

## Functional programming

**Tiny functions:** Save every single line (or few lines) as its own function.

**No consequences except on that line** Each function's only 'consequence' is to have its result given to specifically the lext line of code ('function call') and not to any other lines.

**Recombine/compose** Build up our application by using these small blocks of self-contained code combinging them up line-by-line by _referring to their human-readable name_.

### We could produce a beautiful 'to do list' of our code

```js
pipe(
    getPlayerName,
    getFirstName,
    properCast,
    addUserLabel,
    createUserTemplate
)([{name: 'will sentance', score: 3}]);
```

And render to a webpage.

## Function programming tehcniques - How do we recombine

Combinging our functions is going to require a ton of interesting techniques to:

* rejoin these 'ines' of code (tiny functions) into full-sized tasks
* make it easy to reuse these functions all over the place
* ensure that the tiny functions truly are self-contained

_we're going to see many of these theniques in this document._

### (1) Higher order functions, (2) Function composition

* A lot of these atoms of code (tiny functions) will be reusable
  * They're small enoug hthat they're tasks like incrementing a number, looping through an array
  * We want to wrinte once, use again and again - even for tasks that are not quite identitical - keeping our code dry

### (3) Pure functions, Immutability of state

We cannot have our lines of code rely on any external data except their explicitly stated inputs.

It's especially important when you're reusing/recombinging lots of these little single-step functions in lots of totally different scenarios - they better be self contained!

### (4)Closure, (5) Function Decoration (6) Partial application & Currying

We will need ways to:

* Adjust the functions in case they don't quite fit together as initially saved
* Give our functions extra features without having to write a new function from scratch

### If we can do all that, our code will become

* **More readable**- every line of code has a name that indicates its goal known as 'declarative' programming
* **Easier to debug**- Each line of code is an individual unit with clear input and output - no unexpected consequeences of using that line ('function')
* **Easier to add features**- Most new things we want to do are combination of something we've done elsewhere in our app

### Our and and beginning

Functions become reusable, versatile, flexible piece of code - a series of independent self-contained readable and predictable steps passing data from one to the next

But it all starts with us being condfident with the core principles of JavaScript.
