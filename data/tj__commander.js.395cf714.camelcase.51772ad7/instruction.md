# Bug Report

### Describe the bug

I'm experiencing an issue with the camelcase conversion function. When converting kebab-case strings to camelCase, the output is incorrect - it seems like the first character of each word segment is being duplicated.

### Reproduction

```js
// Example conversions that are producing wrong output:
camelcase('foo-bar')      // Expected: 'fooBar', Getting: 'fooBbar'
camelcase('hello-world')  // Expected: 'helloWorld', Getting: 'helloWworld'
camelcase('my-option')    // Expected: 'myOption', Getting: 'myOoption'
```

The first segment works fine, but subsequent segments after hyphens have their first character appearing twice - once uppercase and once as part of the remaining string.

### Expected behavior

The function should properly convert kebab-case strings to camelCase format:
- `'foo-bar'` → `'fooBar'`
- `'hello-world'` → `'helloWorld'`
- `'my-option-name'` → `'myOptionName'`

### Additional context

This appears to affect any multi-word kebab-case string. Single words without hyphens work correctly.

---
Repository: /testbed
