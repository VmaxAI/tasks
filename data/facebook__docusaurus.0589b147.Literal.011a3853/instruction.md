# Bug Report

### Describe the bug

When using bigint literals in MDX code, the generated output is missing the `n` suffix that's required for JavaScript bigint syntax. This causes the generated code to be invalid JavaScript since bigints must have the trailing `n`.

### Reproduction

```js
// In an MDX file
const largeNumber = 9007199254740991n;
```

After processing through MDX, the generated output produces:
```js
const largeNumber = 9007199254740991;
```

Instead of the expected:
```js
const largeNumber = 9007199254740991n;
```

### Expected behavior

Bigint literals should preserve the `n` suffix in the generated output to maintain valid JavaScript syntax. Without the suffix, the value is treated as a regular number which can lose precision for large integers and will cause syntax errors in strict contexts.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
