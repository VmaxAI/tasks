# Bug Report

### Describe the bug

I'm experiencing an issue with directive parsing where the closing brace of a label is not being properly consumed. The parser seems to be exiting the marker type before consuming the closing brace character, which causes the brace to not be included in the token stream correctly.

### Reproduction

```js
const directive = '[text]{#id}'

// Parse the directive
const result = parse(directive)

// The closing brace '}' is not properly consumed
// Expected the marker to be consumed before exiting
```

### Expected behavior

When parsing a directive label, the closing brace should be consumed as part of the marker token before exiting the marker type. The token sequence should properly include the closing brace character in the marker.

### System Info
- remark-directive version: 3.0.0
- Node version: Latest

---
Repository: /testbed
