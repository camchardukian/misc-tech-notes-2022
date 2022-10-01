# Redux Notes

> “Redux is a pattern and library for managing and updating application state, using events called “actions”.

## Tradeoffs of Using Redux

Using Redux has several drawbacks such as:

- More boilerplate code
- More concepts to learn
- Requires adhering to certain restrictions

With that being said, these tradeoffs may be worth it if:

- We have large amounts of application state that are needed in many places in the app
- The app state is updated frequently over time
- The logic to update state may be complex
- The app has a medium or large-sized codebase that may be worked on by many people

## Key Terms

### State

A broad term that usualy refers to the single state value that is managed by the store and returned by _getState()_

### Store

The center of every Redux application.

The "store" is a JavaScript object that holds our application's global state tree.

In a given Redux app there should only be a single store.

The Redux store has several special functions like:

- dispatch(action)
- getState()
- subscribe(listener)
- replaceReducer(nextReducer)

### Action

A plain object that describes something that happened in the application.

Apart from merely saying what happened, actions also represent an intention to change the state of the application.

Actions are the only way to get data into the store.

All actions must have a "type" field which is a string that indicates the type of action being performed.

An action commonly includes additional information in an optional "payload" field.

### Reducer

A reducer is a function that accepts an accumulation and a value and returns a new accumulation.

Reducers are not unique to Redux, and JavaScript even has a built-in API for reducing _Array.prototype.reduce()_.

In Redux the accumulated value is the state object, and the values being accumulated are actions.

Reducers must be pure functions and free of side effects.

We should also be careful not to mutate state directly inside of our reducers, but to instead copy the existing state and modify the copy.

### Middleware

A middleware is a higher-order function that composes a dispatch function to return a new dispatch function.

Middleware can be useful for logging actions, performing side effects, or turning an async API call into a series of synchronous actions.

### Dispatching

The Redux store has a method called "dispatch".

We update the state of our application by calling _store.dispatch()_ and passing in an action object.

The store will then run its reducer function, save the new state value inside, and we can then call _store.getState()_ to retrieve the updated value.

Conceptually, dispatching actions is like "triggering an event", and the reducers act like event listeners, and when they hear an action they are interested in they're able to update the state in response.

### Selectors

Functions that can be used to extract specific pieces of information from a store state value.

## Data Flow

When first setting up the Redux store, data follows this flow:

1. A Redux store is created using a root reducer function
1. The store calls the root reducer once, and saves the return value as its initial state
1. When the UI is first rendered, UI components access the current state of the Redux store, and use that data to decide what to render. The UI may also subscribe to any future store updates so that it may know if the state has changed

From here, subsequent updates would go like this:

1. Something happens in the app such as a button click or keystroke
1. The app code dispatches an action to the Redux store
1. The store runs the reducer function again with the previous state & current action, and saves the return value as the new state
1. The store notifies all subscribed parts of the UI that the store has been updated
1. Each UI component that needs data from the store checks to see if the parts of the state they need have changed
1. Each component that sees its data has changed forces a re-render with the new data, so it can update what's shown on the screen

## Middleware in More Depth

Redux middleware provides a third-party extension point between dispatching an action, and the moment the action reaches the reducer.

As such, people often use Redux middleware for logging, crash reporting, routing, talking to an asynchronous API, etc.

Typically a middleware will check to see if the action is of a specfic type that it cares about (quite similar to how reducers behave!).

If an action is of the right type, the middleware may run some custom logic, otherwise it will pass the action to the next middleware in the pipeline.

Unlike reducers, middleware can have side effects inside, such as timeouts or other async logic.

## React & Redux

Redux can be used with any UI framework (or even without a framework), but it was specifically designed to work well with React.

Here are the steps that are required to use Redux with any UI layer:

1. Create a Redux store
1. Subscribe to updates
1. Inside the subscription callback:
   - Get the current store state
   - Extract the data needed by this piece of UI
   - Update the UI with the data
1. If necessary, render the UI with initial state
1. Respond to UI inputs by dispatching Redux actions

### React-Redux Hooks

The _React-Redux_ library contains custom hooks that give our React component the ability to read data from the Redux store.

The most common hooks are:

**useSelector** -- Allows us to extract data from the Redux store state, using a selector function.

Selector functions take the entire store state as an argument, and return a value based on that state.

Then, whenever the selector result changes, useSelector forces the component to re-render with the new data.

**useDispatch** -- Returns a reference to the "dispatch" function from the Redux store.

This reference can then be used to dispatch actions as needed.

**useStore** -- Returns a reference to the same Redux store that was passed in to the \<Provider> component.

This hook should not be used frequently, but may occasionally be useful for less common scenarios that _do_ require access to the store, such as replacing reducers.

### React-Redux Patterns

- Global state that is needed across the app should go in the Redux store.

- State that's only needed in one place should be kept in component state.

- It's possible to call useSelector multiple times within one component and doing so is actually a good idea as each call to useSelector should always return the smallest amount of state possible.

- Using action creators to return action objects rather than writing action objects inline is a good practice in larger applications.

- The Redux community commonly adheres to the [Flux Standard Actions (FSA)](https://github.com/redux-utilities/flux-standard-action#motivation) convention when giving actions additional fields beyond just "type".

- When defining state for an "isLoading" value it often makes sense to use a string enum value rather than a boolean.

  This is because with a boolean we can only have "loading" or "not loading" states.

  A more accurate depiction of the state, however, may instead include values such has "not yet started", "in progress", "succeeded", "failed", and "succeeded, but may want to refetch again".

## Asynchronous Code

By default a Redux store doesn't know anything about async logic.

Any asynchronicity has to happen outside the store.

## Redux Toolkit

_Redux Toolkit (RTK)_ is an official opinionated toolset for efficient Redux development.

It includes APIs that simplify most Redux code and wraps around the Redux core.

## Resources

I compiled these notes mostly while reading through the following resources:

https://redux.js.org/tutorials/fundamentals/part-1-overview

https://github.com/redux-utilities/flux-standard-action#motivation
