# Bug Report

### Describe the bug

When using compiler transformations that inject props into components, duplicate props are being added to the props object instead of being prevented. This causes the same prop to appear multiple times in the compiled output, which can lead to unexpected behavior and warnings.

### Reproduction

```js
// Component with props that should be injected
const component = {
  props: {
    modelValue: String,
    // ... other props
  }
}

// When the compiler tries to inject a prop that already exists
// (e.g., during v-model transformation or other directive processing)
// The prop gets added again instead of being skipped
```

The issue occurs when:
1. A prop already exists in the component's props object
2. The compiler attempts to inject the same prop again
3. Instead of skipping the duplicate, it gets added to the props array

### Expected behavior

When a prop already exists in the props object, attempting to inject it again should be skipped to avoid duplicates. The props object should only contain unique property definitions.

### System Info
- Vue version: 3.x
- Compiler: @vue/compiler-core

---
Repository: /testbed
