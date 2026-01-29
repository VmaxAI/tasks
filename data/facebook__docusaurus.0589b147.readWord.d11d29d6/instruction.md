# Bug Report

### Describe the bug

I'm encountering an issue with keyword parsing in the MDX parser. When parsing JavaScript code blocks within MDX files, keywords are not being recognized correctly and seem to be treated as regular identifiers instead.

### Reproduction

```mdx
export const example = () => {
  const result = true;
  if (result) {
    return "success";
  }
}
```

When parsing this MDX content, keywords like `const`, `if`, and `return` are not being handled properly. The parser appears to be mixing up the token type and value, causing syntax errors or incorrect AST generation.

### Expected behavior

Keywords should be correctly identified and parsed with their appropriate token types. The parser should distinguish between keywords (like `if`, `const`, `return`) and regular identifiers.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
