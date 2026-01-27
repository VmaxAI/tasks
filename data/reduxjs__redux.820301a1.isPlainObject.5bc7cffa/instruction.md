# Bug Report

### Describe the bug

I'm encountering an issue where `Object.create(null)` objects are not being recognized as plain objects. These null-prototype objects should be treated as plain objects since they're commonly used for dictionary-like data structures, but the library seems to be rejecting them.

### Reproduction

```js
const nullProtoObj = Object.create(null)
nullProtoObj.foo = 'bar'

// This returns false, but should return true
console.log(isPlainObject(nullProtoObj))
```

### Expected behavior

Objects created with `Object.create(null)` should be recognized as plain objects since they're legitimate plain object instances, just without the default Object prototype. This is a common pattern for creating clean dictionaries without inherited properties.

### Additional context

This is affecting my use case where I'm using null-prototype objects to avoid prototype pollution issues. The library worked fine with these objects in previous versions.

---
Repository: /testbed
