# Bug Report

### Describe the bug

Self-closing JSX tags are not being parsed correctly in MDX files. When I use a self-closing tag like `<Component />`, the parser crashes or doesn't recognize it as valid syntax.

### Reproduction

```mdx
# My Document

<MyComponent />

Some text here.
```

When parsing this MDX content, the self-closing tag `<MyComponent />` causes unexpected behavior. The parser seems to reject the `>` character after the self-closing slash.

### Expected behavior

Self-closing JSX tags should be properly recognized and parsed. The syntax `<Component />` is standard JSX and should work in MDX files without issues.

### Additional context

This affects any self-closing JSX tag in MDX content. Regular opening/closing tag pairs like `<Component></Component>` seem to work fine, but the self-closing shorthand syntax doesn't.

---
Repository: /testbed
