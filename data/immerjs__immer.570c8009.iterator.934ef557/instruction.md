# Bug Report

### Describe the bug

After a recent update, iterating over Map entries using the `entries()` method is completely broken. The iterator doesn't return any key-value pairs and the application crashes when trying to use `for...of` loops or spread operators on Map entries.

### Reproduction

```js
const map = new Map([
  ['key1', 'value1'],
  ['key2', 'value2']
])

// This fails to iterate properly
for (const [key, value] of map.entries()) {
  console.log(key, value)
}

// Spreading entries also doesn't work
const entries = [...map.entries()]
```

### Expected behavior

The `entries()` method should return an iterator that yields `[key, value]` pairs for each entry in the Map. It should work correctly with `for...of` loops and other iteration patterns.

### System Info
- Version: Latest
- Node: v18.x

This is blocking our production deployment as we rely heavily on Map iteration throughout the codebase.

---
Repository: /testbed
