# Bug Report

### Describe the bug

The `subscribe` method is not working properly with observer objects. When I pass a valid observer object with a `next` method, it throws a TypeError saying it expected an object, even though I'm clearly passing one.

### Reproduction

```js
const store = createStore(reducer, initialState);

const observer = {
  next: (state) => {
    console.log('State updated:', state);
  }
};

// This throws an error unexpectedly
store.subscribe(observer);
```

### Expected behavior

The observer should be registered successfully and receive state updates through its `next` method when the store changes. The subscription should work without throwing any errors when a valid observer object is passed.

### Additional context

This seems to have started recently. The error message is confusing because I am passing an object, but it's still complaining about the type. Also noticed that even if I could get past this error, the `next` callback doesn't seem to be getting called when it should be.

---
Repository: /testbed
