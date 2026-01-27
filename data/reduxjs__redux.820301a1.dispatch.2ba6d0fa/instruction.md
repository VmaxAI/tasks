# Bug Report

### Describe the bug
After a recent update, I'm getting syntax errors when trying to use Redux middleware. The application fails to compile and throws errors about unexpected Python code in a TypeScript file.

### Reproduction
```js
import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'

const store = createStore(
  rootReducer,
  applyMiddleware(thunk)
)
```

When I try to build or run my app, I get compilation errors pointing to the `applyMiddleware.ts` file. It looks like there's Python code mixed into the TypeScript source somehow?

### Expected behavior
The store should be created successfully with middleware applied, and the application should compile without errors.

### System Info
- Redux version: latest
- Node: 18.x
- TypeScript: 5.x

---
Repository: /testbed
