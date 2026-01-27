# Bug Report

### Describe the bug

I'm experiencing an issue with component hierarchy where child components are not properly inheriting the `provides` object from their parent components. It seems like the provide/inject mechanism is broken in nested component structures.

### Reproduction

```js
// Parent component
const Parent = {
  setup() {
    provide('theme', 'dark')
    return () => h(Child)
  }
}

// Child component
const Child = {
  setup() {
    const theme = inject('theme')
    console.log(theme) // Expected: 'dark', Actual: undefined
    return () => h('div', theme)
  }
}
```

### Expected behavior

Child components should be able to inject values that were provided by their parent components. The `provides` object should be properly inherited down the component tree.

### Additional context

This appears to affect the entire provide/inject API. When a parent component provides a value, child components are unable to access it through `inject()`. The inheritance chain seems to be broken somewhere in the component initialization.

---
Repository: /testbed
