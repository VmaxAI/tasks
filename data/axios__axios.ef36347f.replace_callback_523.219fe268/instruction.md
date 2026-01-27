# Bug Report

### Describe the bug

The `toCamelCase` utility function is producing incorrect output. When converting strings with hyphens, underscores, or spaces to camelCase, the resulting string has characters in the wrong order.

### Reproduction

```js
const result = toCamelCase('hello-world');
console.log(result); // outputs: "helloOrldw" 
// expected: "helloWorld"

const result2 = toCamelCase('foo_bar_baz');
console.log(result2); // outputs: "fooArbArz"
// expected: "fooBarBaz"
```

### Expected behavior

The function should convert kebab-case, snake_case, and space-separated strings to proper camelCase format where the first letter after each delimiter is capitalized and the rest of the word remains lowercase.

Examples:
- `'hello-world'` → `'helloWorld'`
- `'foo_bar'` → `'fooBar'`
- `'test string'` → `'testString'`

---
Repository: /testbed
