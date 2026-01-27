# Bug Report

### Describe the bug

The `kindOf` utility function is returning incorrect type strings for certain objects. When checking the type of various JavaScript values, I'm getting unexpected results that don't match the actual types.

### Reproduction

```js
import { miniKindOf } from './utils/kindOf'

// Testing with different values
console.log(miniKindOf([1, 2, 3]))           // Expected: 'array', Got: 'object'
console.log(miniKindOf(new Date()))          // Expected: 'date', Got: 'object'
console.log(miniKindOf(new Error('test')))   // Expected: 'error', Got: 'object'
console.log(miniKindOf(/regex/))             // Expected: 'regexp', Got: 'object'
console.log(miniKindOf(new Map()))           // Expected: 'map', Got: 'object'
console.log(miniKindOf(new Set()))           // Expected: 'set', Got: 'object'
```

### Expected behavior

The function should return the correct type string for each JavaScript value:
- Arrays should return `'array'`
- Date objects should return `'date'`
- Error objects should return `'error'`
- RegExp objects should return `'regexp'`
- Map objects should return `'map'`
- Set objects should return `'set'`

Instead, everything is just returning `'object'` now.

### Additional context

This seems to have broken after a recent update. The type detection logic appears to be short-circuiting and returning `'object'` too early, preventing the more specific type checks from running.

---
Repository: /testbed
