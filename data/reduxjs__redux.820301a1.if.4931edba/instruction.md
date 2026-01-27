# Bug Report

### Describe the bug

When calling `createStore()` with a function as the second argument (intended as `preloadedState`) and also providing an `enhancer` as the third argument, the store is created incorrectly. The `preloadedState` function gets incorrectly assigned as the enhancer, even though an explicit enhancer was already provided.

### Reproduction

```js
const reducer = (state = {}, action) => state;
const preloadedStateFunc = () => ({ count: 0 });
const myEnhancer = (createStore) => (reducer, preloadedState) => {
  // custom enhancer logic
  return createStore(reducer, preloadedState);
};

// This doesn't work as expected
const store = createStore(
  reducer,
  preloadedStateFunc,  // This should be used as preloadedState
  myEnhancer           // This should be used as enhancer
);
```

### Expected behavior

When both a function `preloadedState` and an `enhancer` are provided, the store should:
1. Use the function as `preloadedState` 
2. Use the third argument as the `enhancer`
3. Not swap or override the enhancer with the preloadedState function

Currently it seems like the logic is treating the `preloadedState` function as an enhancer even when an explicit enhancer is already passed.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
