# Bug Report

### Describe the bug

I'm experiencing an issue with MDX JSX attribute parsing where attribute names are being assigned to the wrong attribute node. When parsing JSX tags with multiple attributes, the attribute name gets applied to an incorrect element in the attributes array.

### Reproduction

```jsx
<Component 
  firstAttr="value1"
  secondAttr="value2"
/>
```

When parsing the above JSX, the attribute names don't get assigned to the correct attribute objects. It seems like the parser is looking at the wrong index in the attributes array.

### Expected behavior

Each attribute name should be correctly assigned to its corresponding attribute node in the order they appear. The `firstAttr` name should be assigned to the first attribute, `secondAttr` to the second, and so on.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
