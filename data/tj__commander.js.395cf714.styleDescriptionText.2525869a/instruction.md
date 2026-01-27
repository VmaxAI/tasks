# Bug Report

### Describe the bug

I'm experiencing an issue with help text display in my CLI application. Description text that starts with capital letters or spaces is getting truncated - the first character is being removed. Additionally, any description text containing a colon (`:`) character is completely disappearing and showing as blank.

### Reproduction

```js
// Description starting with capital letter
const option1 = {
  description: 'Enable verbose output mode'
}
// Expected: "Enable verbose output mode"
// Actual: "nable verbose output mode"

// Description with colon
const option2 = {
  description: 'Format: JSON or XML'
}
// Expected: "Format: JSON or XML"
// Actual: "" (empty string)

// Description starting with space
const option3 = {
  description: ' Indented description text'
}
// Expected: " Indented description text"
// Actual: "Indented description text"
```

### Expected behavior

Description text should be displayed exactly as provided without any character removal or filtering. Colons should be preserved as they're commonly used in help text (e.g., "Usage:", "Format:", etc.).

### System Info
- Node version: 18.x
- OS: macOS

This seems to have started happening recently. The help text was displaying correctly before.

---
Repository: /testbed
