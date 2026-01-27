# Bug Report

### Describe the bug

I'm experiencing an issue with warning handlers in Vue 3. When a warning is triggered from a deeply nested component, the `warnHandler` receives the wrong component instance - it seems to be getting the root component instead of the actual component that triggered the warning.

### Reproduction

```js
const app = createApp({
  template: '<Parent />'
})

app.config.warnHandler = (msg, instance, trace) => {
  console.log('Warning from:', instance?.type.name)
  // Expected: 'ChildComponent'
  // Actual: 'RootComponent' or parent component
}

// Component hierarchy:
// Root -> Parent -> Child
// Warning triggered in Child component
```

### Steps to reproduce:
1. Set up a component hierarchy with nested components
2. Configure a custom `warnHandler` 
3. Trigger a warning from a deeply nested child component
4. Check which component instance is passed to the handler

### Expected behavior

The `warnHandler` should receive the component instance that actually triggered the warning (the innermost/current component in the stack), not a parent or root component.

### System Info
- Vue version: 3.x

This makes it really difficult to debug warnings in larger applications since the handler points to the wrong component context.

---
Repository: /testbed
