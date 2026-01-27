# Bug Report

### Describe the bug

I'm experiencing an issue with template compilation where the first character of certain strings seems to be getting dropped or ignored during parsing. This is causing templates to render incorrectly or fail to compile properly.

### Reproduction

```js
// When compiling templates with specific text content
const template = `<div>Hello World</div>`

// The compiled output seems to be missing the first character
// Expected: "Hello World"
// Actual: "ello World" (or similar truncation)
```

This appears to affect any string-based content in templates, particularly text nodes and attribute values. The issue manifests as:
- Text content missing its first character
- Attribute values being truncated
- Potential parsing errors when the first character is significant

### Expected behavior

Template strings should be processed completely without losing any characters. All text content and attributes should render exactly as written in the source template.

### System Info
- Vue version: 3.x
- Build tool: Vite

Has anyone else encountered this? It seems like a character encoding or buffer issue in the compiler.

---
Repository: /testbed
