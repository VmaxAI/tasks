# Bug Report

### Describe the bug

I'm experiencing an issue with JSX tag parsing where the closing bracket of JSX tags seems to be causing problems with the token stream. After parsing a JSX tag, the parser state appears to be corrupted or in an unexpected state.

### Reproduction

```jsx
<Component />
```

When parsing JSX elements with self-closing tags or regular closing tags, the parser doesn't properly handle the end marker. This affects how subsequent content is processed.

### Expected behavior

JSX tags should be parsed correctly and the token stream should be properly structured after encountering the closing `>` bracket. The parser should exit the tag state cleanly without leaving orphaned token entries.

### System Info
- remark-mdx version: 3.0.0

---
Repository: /testbed
