# Bug Report

### Describe the bug

I'm encountering an issue with the MDX parser where escape sequences in keywords are not being properly validated. The parser seems to be raising errors for escape sequences even when they shouldn't be flagged.

### Reproduction

When parsing MDX content that contains keywords, the parser incorrectly reports escape sequence errors. This appears to be related to how the parser checks for escape sequences in keyword tokens.

```js
// Example MDX content that triggers the issue
const mdxContent = `
export const myKeyword = "value"
`

// Parser raises error about escape sequences incorrectly
```

The error message mentions "Escape sequence in keyword" but occurs in cases where there's no actual escape sequence in the keyword itself.

### Expected behavior

The parser should only raise errors when there's actually an escape sequence within a keyword token, not when `containsEsc` is true for other reasons.

### Additional context

This seems to have started happening recently. The validation logic appears to be checking the wrong condition when determining whether to raise the escape sequence error.

---
Repository: /testbed
