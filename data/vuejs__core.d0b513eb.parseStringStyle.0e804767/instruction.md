# Bug Report

### Describe the bug

I'm encountering an issue with inline style parsing when using CSS properties that contain colons in their values. The style string is not being parsed correctly and some properties are getting lost or mangled.

### Reproduction

```js
// Example with a CSS custom property or url() that contains colons
const styleString = 'background: url(https://example.com/image.png); color: red;'
const parsed = parseStringStyle(styleString)

// The background property doesn't parse correctly
console.log(parsed)
// Expected: { background: 'url(https://example.com/image.png)', color: 'red' }
// Actual: Properties are missing or incorrectly parsed
```

Another case:
```js
const styleString = 'content: "Hello: World"; font-size: 16px;'
const parsed = parseStringStyle(styleString)
// The content property with colon in the string value breaks parsing
```

### Expected behavior

Style strings with multiple colons (like in URLs, custom properties, or string content) should be parsed correctly, preserving all property-value pairs.

### System Info
- Vue version: 3.x
- Affects inline style binding

---
Repository: /testbed
