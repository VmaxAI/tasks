# Bug Report

### Describe the bug

I'm encountering an issue with template parsing where attribute values in quotes are being incorrectly parsed. It seems like the opening quote character is being included as part of the attribute value itself.

### Reproduction

When parsing HTML/template strings with quoted attribute values, the quotes are being included in the parsed value:

```js
// Template with double-quoted attribute
<div title="hello"></div>

// Expected parsed value: "hello"
// Actual parsed value: "\"hello"

// Same issue with single quotes
<div title='world'></div>

// Expected parsed value: "world"  
// Actual parsed value: "'world"
```

### Expected behavior

The parser should extract the attribute value without including the opening quote character. The quote should only be used to delimit the value, not be part of the value itself.

### Additional context

This affects both single and double quoted attributes. Unquoted attribute values seem to work fine. This is causing issues in my components where attribute values are being rendered with extra quote characters at the beginning.

---
Repository: /testbed
