# Bug Report

### Describe the bug

The `merge()` utility function is not creating deep copies of arrays when merging objects. When merging objects that contain arrays, the resulting object shares references to the original arrays instead of creating independent copies. This means modifying arrays in the merged result also modifies the original arrays.

### Reproduction

```js
const obj1 = {
  items: [1, 2, 3]
};

const obj2 = {
  name: 'test'
};

const merged = merge(obj1, obj2);

// Modifying the merged array also modifies the original
merged.items.push(4);

console.log(obj1.items); // Expected: [1, 2, 3], Actual: [1, 2, 3, 4]
```

### Expected behavior

The merge function should create independent copies of arrays so that modifications to the merged result don't affect the original objects. Arrays should be treated similarly to plain objects and be deeply cloned.

### Additional context

This is causing issues when trying to create immutable state updates, as the original state gets unintentionally mutated through shared array references.

---
Repository: /testbed
