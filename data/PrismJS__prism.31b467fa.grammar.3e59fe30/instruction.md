# Bug Report

### Describe the bug

I'm experiencing an issue with date/time string pattern matching in the BSL (1C:Enterprise) language syntax highlighting. The pattern for date and time strings appears to be incomplete or truncated, causing strings to be incorrectly highlighted or not highlighted at all.

### Reproduction

```js
// Date & time string in 1C:Enterprise
'2024-01-15T10:30:00'

// The pattern should match date/time strings but it seems broken
```

When using date/time strings in BSL code, the syntax highlighting doesn't work as expected. The pattern seems to be cut off or malformed.

### Expected behavior

Date and time strings (enclosed in single quotes) should be properly recognized and highlighted according to the BSL language syntax rules. The pattern should correctly match strings like `'2024-01-15T10:30:00'` or similar date/time formats used in 1C:Enterprise.

### System Info
- Language: BSL (1C:Enterprise)
- Issue appears to be in the grammar definition

---
Repository: /testbed
