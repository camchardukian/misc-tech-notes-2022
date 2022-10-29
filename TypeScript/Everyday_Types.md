# Everyday Types

## Primitives

In JavaScript there are 7 primitives data types:

- string
- number
- bigint
- boolean
- undefined
- symbol
- null

In the context of JS a primitive is data that is not an object and that has no methods or properties.

The reason primitives may appear to have methods and properties is that JavaScript boxes these primitive data types into various objects (such as the `String` object).

All of the primitive data types in JS are immutable.

## String, Number, & Boolean

The 3 most commonly used primitives in JavaScript are `string`, `number`, and `boolean`.

These three primitives have corresponding types of `string`, `number`, and `boolean`.

While capitalized `String`, `Number`, and `Boolean` types exist, they are used much more rarely.

## Arrays

We can specify an array of numbers using two different syntaxes:

1. `number[]`
1. `Array<number>`

A similar syntax works for arrays of strings and other types as well.

## Any

The `any` type can be used to essentially opt-out of type-checking and revert to standard JavaScript for a given piece of code.

It's recommended to use the `any` type for cases where we don't know what the shape of type of something will be.

For example, if we receive a function argument from a third-party library written in plain JavaScript we may not know with certainty the type of the argument provided to us.

## Type Annotation Order

Type annotations will always go after the thing being typed.

## Functions

### Parameter Type Annotations

Parameter type annotations go after the parameter name.

Even if we don't add type annotations to our parameters, TypeScript will still check that we passed the correct number of arguments.

### Return Type Annotations

Return type annotations may be declared after the parameter list.

## Object Types

To define an object type we simply list its properties and their types.

We can use `,` or `;` to separate each property.

## Union Types

A _union_ type is a type formed from two or more other types.

A union type basically indicates that something will be of one of the types that were combined to form the union.

If we have a union type, TypeScript will only allow operations that are valid for every member of the union.

## Type Aliases

A _type alias_ is a name for any type.

## Type Aliases vs Interfaces

As a general rule, it's recommended to default to using _interfaces_ until we need some specific functionality that only _type aliases_ can provide.

One difference between the two is that only interfaces support declaration merging.

On the other hand, type alliases are sometimes better for simpler syntax, working with primitives, and using unions.

## StrictNullChecks

By turning on _strictNullChecks_, when a value is `null` or `undefined` we will be forced to test for those values before using methods or properties on that value.

## BigInt

From ES2020 onwards the primitive `BigInt` can be used for very large numbers. `BigInt` has a corresponding type of `bigint`.

## Resources

1. [Everyday Types](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html)

1. [Primitives](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)

1. [TypeScript Types vs Interfaces](https://www.youtube.com/watch?v=IXAT3If0pGI)
