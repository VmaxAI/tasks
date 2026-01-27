# Bug Report

### Describe the bug

When using inline styles with non-string and non-number values, the styles are being incorrectly included in the rendered output. According to Vue's behavior, only string and number values should be rendered as valid CSS values, but other types (like objects, arrays, booleans, etc.) are now appearing in the style string.

### Reproduction

```js
const styles = {
  color: 'red',
  width: 100,
  display: true,  // Should be filtered out
  background: { gradient: 'linear' },  // Should be filtered out
  padding: null  // Should be filtered out
}

const result = stringifyStyle(styles)
// Currently outputs: "color:red;width:100;display:true;background:[object Object];padding:null;"
// Expected: "color:red;width:100;"
```

### Expected behavior

Only string and number values should be included in the stringified style output. Other value types (booleans, objects, arrays, null, undefined) should be filtered out and not rendered.

### System Info
- Vue version: 3.x

This seems to have started recently - inline styles with invalid value types are now being rendered instead of being filtered out properly.

---
Repository: /testbed
