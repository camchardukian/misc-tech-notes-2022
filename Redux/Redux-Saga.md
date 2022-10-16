# Redux Saga

Redux Saga is a middleware library.

Redux Saga is useful because it gives us a place inside of Redux to put our side effects.

## Generator Functions

Generators are functions which can be exited and later re-entered. Their context (variable bindings) will be saved across re-entrances.

Generator functions can be identified by the _function\*_ declaration (the function keyword followed by an asterisk).

Generator functions return Generator objects.

Generator objects have a _value_ property and a _done_ property.

Whenever we run a generator function, we create a unique generator object to iterate on.

Generator objects can be useful for running infinite loops or iterators.

Whatever is passed to the Generator object's .next() function will be returned the next time the generator function executes and comes across the _yield_ keyword.

If we call .return() on a Generator object, we will set its _done_ property to true.

The _yield\*_ keyword (yield followed by an asterisk) is used to delegate to another outside generator function.

ES7 introduced async generators.

## Sagas

In Redux-Saga, Sagas are implemented using Generator functions.

To express Saga logic we yield plain JavaScript objects from the Generator.

In the context of Redux Saga, these JS objects are called _Effects_.

## Effects

An Effect is an object that contains information to be interpreted by the middleware.

Effects are like instructions to the middleware to perform some operation.

To create Effects, we can use the functions provided in the _redux-saga/effects_ package.

For example, the _call_ function can be imported from the above package, and _call_ can be used to create a plain object describing the Effect (function call) we will later want to execute.

The _redux-saga/effects_ library also has another function _put_ which can be used to create a dispatch Effect.

## Error Handling

We can catch errors inside our Sagas using the familiar _try/catch_ syntax.

In Redux-Saga, errors from child tasks bubble up until the errors are caught or they reach the root saga.

## Saga Helpers

We can use the _takeEvery_ helper inside of our "watcher" saga if we want multiple instances of our task saga to be able to be started concurrently.

Otherwise, if we only want to get the response of the latest request fired (such as if we only wanted to display the latest version of data), we could use the _takeLatest_ helper.

## Advanced Concepts

We can use the _yield_ keyword to yield to multiple tasks in an array simultaneously.

For example:

```
const results = yield all([call(task1), call(task2)])

yield put (showResults(results))
```

The _race_ Effect, allows us to start multiple tasks in unison but to only take the results of the first task to resolve/reject.

## Resources

1. [Introduction to Redux Saga](https://www.loginradius.com/blog/engineering/introduction-to-redux-saga/)

1. [Learn Javascript Generators in 12 Minutes](https://www.youtube.com/watch?v=IJ6EgdiI_wU)

1. [The Power of JS Generators](https://www.youtube.com/watch?v=gu3FfmgkwUc)

1. [Redux Saga Docs](https://redux-saga.js.org/docs/basics/DeclarativeEffects)
