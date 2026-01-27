# Bug Report

### Describe the bug

I'm experiencing an issue with type detection for objects with custom constructors. When I create an object using a custom constructor function, the type detection seems to be returning incorrect results.

### Reproduction

```js
function CustomType() {
  this.value = 42;
}

const instance = new CustomType();

// Type detection doesn't work as expected
// Should detect the constructor name "CustomType" but doesn't seem to work correctly
console.log(kindOf(instance)); 
```

The issue appears when working with objects that have constructor functions. The library should be able to identify the constructor name, but it's not behaving as expected.

### Expected behavior

The type detection should correctly identify objects created with custom constructors and return the constructor name. This was working fine in previous versions.

### Additional context

This seems to have started happening recently. Not sure if this is related to recent changes in the type detection logic, but it's affecting my ability to properly identify custom types in my application.

---
Repository: /testbed
