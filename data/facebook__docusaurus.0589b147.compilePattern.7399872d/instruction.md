# Bug Report

### Describe the bug

I'm experiencing an issue with markdown serialization where certain special characters are being escaped incorrectly. Characters that should be escaped are not being escaped, and characters that shouldn't be escaped are getting escape sequences added.

### Reproduction

```js
// Try serializing markdown with special characters
const markdown = {
  type: 'text',
  value: 'some text with - or . characters'
}

// The output incorrectly escapes these characters
// Expected: "some text with - or . characters"
// Actual: "some text with \- or \. characters"
```

When using the markdown serializer, regular characters like hyphens and periods are being escaped with backslashes even though they don't need to be in most contexts. This makes the output harder to read and causes issues when the markdown is parsed again.

### Expected behavior

Special characters should only be escaped when they have special meaning in markdown syntax. Regular punctuation like `-` and `.` shouldn't be escaped unless they're in a position where they would be interpreted as markdown syntax (like at the start of a line for lists).

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
