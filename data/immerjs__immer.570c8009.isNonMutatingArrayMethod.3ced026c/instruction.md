# Bug Report

### Describe the bug

After a recent update, I'm getting syntax errors when trying to use array methods on reactive arrays. The application fails to compile/run and throws errors about unexpected syntax.

### Reproduction

```js
const items = reactive(['a', 'b', 'c'])

// Trying to use non-mutating array methods
const filtered = items.filter(item => item !== 'b')
const mapped = items.map(item => item.toUpperCase())
```

The code won't even run - it seems like there's a compilation issue in the arrayMethods plugin itself.

### Expected behavior

Non-mutating array methods like `filter`, `map`, `slice` etc. should work normally on reactive arrays without any compilation errors.

### System Info
- Version: latest
- Node: 18.x

This is blocking my development as I can't use any array operations anymore. Would really appreciate a quick fix!

---
Repository: /testbed
