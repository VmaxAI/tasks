# Bug Report

### Describe the bug

I'm experiencing an issue with type detection in the library. When working with objects that have constructors, the type information seems to be returned incorrectly or incompletely.

### Reproduction

```js
class CustomClass {
  constructor() {
    this.value = 42;
  }
}

const instance = new CustomClass();

// Expected to get the constructor name 'CustomClass'
// But getting unexpected results instead
const result = kindOf(instance);
console.log(result); // Not returning expected type information
```

### Expected behavior

When checking the type of an object with a custom constructor, it should return the constructor name as a string (e.g., `'CustomClass'`). Currently it seems to be returning something else entirely.

### Additional context

This seems to affect any object with a constructor function. Built-in types like `Date`, `RegExp`, etc. might also be impacted. The type detection was working fine in previous versions but broke recently.

---
Repository: /testbed
