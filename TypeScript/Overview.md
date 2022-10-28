# TypeScript Overview

TypeScript is an open source language that is a superset of JavaScript.

The main reason to use TypeScript is to add static types to JavaScript.

## Dynamic vs Static Typing

**Dynamically typed languages** -- Types are associated with run-time values and not named explicitly in your code. Examples include Java, C, C++, Rust, Go, etc.

**Statically typed languages** -- Types are explicitly assigned to variables, function parameters, return values, etc. Examples include JavaScript, Python, Ruby, PHP, etc.

## Pros & Cons of Using TypeScript

**Pros**:

- More robust code
- Easily spot bugs
- Predictability
- Readability
- Popular

**Cons**:

- More code to write
- More things to learn
- Requires compilation
- Not true static typing

## Types by Inference

When creating a variable and assigning it to a particular value, TypeScript will use the value as that variable's type.

## Defining Types

We can create interfaces and assign them to our variables, function parameters, etc.

The most common types used in interfaces are:

- number
- string
- null
- undefined
- boolean
- symbol
- unknown
- never
- void

## Composing Types

We can create complex types in TypeScript either by using _unions_ or _generics_.

### Unions

Unions are commonly used to describe the set of string or number literals that a value it allowed to be. For example:

```
type WindowStates = "open" | "closed" | "minimized"
```

Unions also provide the ability to handle different types:

```
function getLength(obj: string | string[]) {
  return obj.length;
}
```

### Generics

Generics provide variables to types. We could for example use generics to indicate the values that an array should contain:

```
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObjectWithNameArray = Array<{ name: string }>;
```

### TypeScript Compiler

We can install the TypeScript compiler by running:

> npm install -g typescript

We can run the TypeScript Compiler with the `tsc` command along with the name of our file. For example: `tsc helloWorld.ts`

After running the above command our current directory will contain a new JavaScript file `helloWorld.js` that was compiled from the TypeScript file.

### Downleveling

When TypeScript compiles code down to JavaScript it targets ES3 by default.

This is configurable using the `target` option.

This process of moving from a newer/higher level of ECMAScript to an older/lower level is sometimes called downleveling.

## Resources

1. [TypeScript Docs](https://www.typescriptlang.org/docs/)
1. [TypeScript Crash Course](https://www.youtube.com/watch?v=BCg4U1FzODs)
