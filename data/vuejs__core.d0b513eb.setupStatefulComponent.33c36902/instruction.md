# Bug Report

### Describe the bug

I'm encountering an issue with the Composition API where the setup context is being created even when the setup function doesn't accept any parameters. This seems to be causing unnecessary overhead and potentially unexpected behavior.

### Reproduction

```js
export default {
  setup() {
    // setup function with no parameters
    // but context is still being created internally
    return {
      message: 'Hello'
    }
  }
}
```

The setup context should only be created when the setup function actually expects it as a second parameter, but it appears to be created regardless.

### Expected behavior

The setup context should only be instantiated when `setup.length > 1`, meaning the function signature indicates it expects both props and context parameters. When setup takes 0 or 1 parameters, no context should be created to avoid unnecessary processing.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
