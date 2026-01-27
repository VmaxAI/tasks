# Bug Report

### Describe the bug

The error URLs generated in production builds are pointing to the wrong location. When an error occurs in production, the URL that's supposed to help debug the issue doesn't work correctly.

### Reproduction

```js
// Trigger any Redux error in production mode
// For example, dispatch an action with undefined type

const store = createStore(reducer)
store.dispatch({ type: undefined })
```

The error message shows:
```
Minified Redux error #1; visit http://redux.js.org/Errors?code=1 for the full message or use the non-minified dev environment for full errors.
```

However, the URL format appears incorrect - it's using `http://` instead of `https://` and the code parameter seems to be formatted differently than expected.

### Expected behavior

The error message should contain a valid URL that points to the correct error documentation page with the proper error code format.

### System Info
- Redux version: latest
- Environment: Production build

---
Repository: /testbed
