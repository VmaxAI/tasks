# Bug Report

### Describe the bug

I'm encountering an issue with MDX parsing where `export` statements are not being recognized correctly. It seems like any statement starting with `export` followed by a space is being treated as valid MDX ESM syntax, even when it shouldn't be.

### Reproduction

```mdx
exportable content here
```

The parser incorrectly accepts this as valid MDX ESM syntax when it should only accept actual `export` statements like:

```mdx
export const foo = 'bar'
```

### Expected behavior

The parser should only recognize valid `export` statements (the keyword `export` followed by a space and valid export syntax). Random words starting with "export" should not trigger the ESM parsing logic.

### System Info
- remark-mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
