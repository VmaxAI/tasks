# Bug Report

### Describe the bug

I'm experiencing an issue with inline style parsing where CSS properties and values appear to be swapped. When I pass a style string to a component, the property names end up as values and vice versa.

### Reproduction

```js
const styleString = 'color: red; font-size: 16px'
const parsed = parseStringStyle(styleString)

console.log(parsed)
// Expected: { color: 'red', 'font-size': '16px' }
// Actual: { red: 'color', '16px': 'font-size' }
```

When applying styles like `style="background-color: blue; padding: 10px"`, the rendered element ends up with completely incorrect styles. The CSS property names and their values are reversed.

### Expected behavior

Style strings should be parsed correctly with property names as keys and their corresponding values as the object values. The current behavior makes it impossible to apply inline styles properly.

### System Info
- Vue version: 3.x
- Browser: Firefox/Chrome

---
Repository: /testbed
