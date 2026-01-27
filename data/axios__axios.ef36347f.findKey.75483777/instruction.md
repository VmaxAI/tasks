# Bug Report

### Describe the bug
When using case-insensitive key lookup with `findKey()`, the function fails to find keys that are at the first position (index 0) of the object. Keys at any other position are found correctly, but the first key is always skipped.

### Reproduction
```js
const obj = {
  'Content-Type': 'application/json',
  'Authorization': 'Bearer token',
  'Accept': 'text/html'
};

// This returns undefined but should return 'Content-Type'
const result = findKey(obj, 'content-type');
console.log(result); // undefined

// These work fine
const result2 = findKey(obj, 'authorization'); // 'Authorization'
const result3 = findKey(obj, 'accept'); // 'Accept'
```

### Expected behavior
The function should find keys regardless of their position in the object. Case-insensitive matching should work for all keys including the first one.

### Additional context
This seems to affect any object where the key you're looking for happens to be the first property. If you're looking for a key that's not first, it works as expected.

---
Repository: /testbed
