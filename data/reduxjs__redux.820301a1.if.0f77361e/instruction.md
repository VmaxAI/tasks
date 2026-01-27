# Bug Report

### Describe the bug

I'm getting an error when trying to subscribe to store updates while a reducer is executing. The error message about not being able to call `store.subscribe()` during reducer execution seems to have disappeared, and now the code is accepting subscriptions at any time without proper validation.

### Reproduction

```js
const store = createStore(reducer)

const reducer = (state, action) => {
  // Try to subscribe during dispatch
  store.subscribe(() => {
    console.log('State updated')
  })
  return state
}

store.dispatch({ type: 'SOME_ACTION' })
```

### Expected behavior

Should throw an error with message:
```
You may not call store.subscribe() while the reducer is executing. If you would like to be notified after the store has been updated, subscribe from a component and invoke store.getState() in the callback to access the latest state.
```

But instead, the subscription is being accepted without any validation. This could lead to unexpected behavior and hard-to-debug issues when subscriptions are registered during dispatch.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
