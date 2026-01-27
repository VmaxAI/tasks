# Bug Report

### Describe the bug

I'm experiencing inconsistent behavior with type detection between development and production builds. In production, I'm getting more detailed type information (like "array", "object", "null") but in development mode, I'm only getting the basic JavaScript `typeof` results (like "object" for arrays and null).

This is causing issues where code that works fine in production breaks in development, which is the opposite of what I'd expect. It seems like the type checking logic might be inverted?

### Reproduction

```js
const arr = [1, 2, 3]
const obj = { key: 'value' }
const nullVal = null

// In production: returns "array", "object", "null" (detailed)
// In development: returns "object", "object", "object" (basic typeof)
console.log(kindOf(arr))
console.log(kindOf(obj))
console.log(kindOf(nullVal))
```

### Expected behavior

Development builds should provide the more detailed type information for better debugging, while production could use the simpler/faster `typeof` check. Currently it seems backwards.

### System Info
- Node version: 18.x
- Build environment: Webpack 5

---
Repository: /testbed
