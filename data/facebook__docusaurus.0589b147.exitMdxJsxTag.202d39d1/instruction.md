# Bug Report

### Describe the bug

I'm encountering an issue with MDX JSX tag parsing where closing tags are being incorrectly validated. It seems like all closing tags are now throwing errors about tag mismatches, even when they correctly match their opening tags.

### Reproduction

```mdx
<MyComponent>
  Some content here
</MyComponent>
```

When parsing this MDX content, I get an error like:
```
Unexpected closing tag `</MyComponent>`, expected corresponding closing tag for `<MyComponent>` (1:1-1:14)
```

Even though the closing tag matches the opening tag perfectly, the parser is throwing a mismatch error.

### Expected behavior

The parser should successfully parse matching opening and closing tags without throwing errors. Only actual mismatches (like `<Foo>...</Bar>`) should trigger validation errors.

### System Info
- remark-mdx version: 3.0.0
- Node version: 18.x

This seems to have broken after a recent update. Any MDX content with properly matched tags is now failing to parse.

---
Repository: /testbed
