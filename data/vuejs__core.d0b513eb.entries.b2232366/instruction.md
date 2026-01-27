# Bug Report

### Describe the bug

I'm encountering an issue with the `entries()` method on reactive arrays. When iterating over a reactive array using `entries()`, the returned values are incorrect - instead of getting `[index, value]` tuples, I'm only getting the index.

### Reproduction

```js
const arr = reactive(['a', 'b', 'c'])

for (const [index, value] of arr.entries()) {
  console.log(index, value)
  // Expected: 0 'a', 1 'b', 2 'c'
  // Actual: 0 undefined, 1 undefined, 2 undefined
}
```

Or using the iterator directly:

```js
const arr = reactive(['foo', 'bar'])
const iter = arr.entries()

console.log(iter.next().value)
// Expected: [0, 'foo']
// Actual: 0 (just the index, not a tuple)
```

### Expected behavior

The `entries()` method should return an iterator that yields `[index, value]` tuples for each element in the array, just like the native Array.prototype.entries() method does.

### System Info

- Vue version: 3.x
- Environment: Node.js

This seems to have broken recently, as it was working fine before. The iterator only returns the index now instead of the full entry tuple.

---
Repository: /testbed
