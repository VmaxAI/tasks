# Bug Report

### Describe the bug

I'm experiencing an issue with MDX JSX tag parsing where attributes in opening tags are being incorrectly rejected. When I try to use JSX components with attributes in my MDX files, I'm getting an error about "Unexpected attribute in closing tag" even though I'm clearly using an opening tag.

### Reproduction

```mdx
<MyComponent foo="bar" />
```

or

```mdx
<MyComponent foo="bar">
  content
</MyComponent>
```

Both of these throw an error:
```
Unexpected attribute in closing tag, expected the end of the tag
```

This is happening with standard JSX component syntax that should be valid. The error message itself is confusing because I'm not even using a closing tag in the first example, and in the second example the attribute is on the opening tag, not the closing tag.

### Expected behavior

JSX components with attributes should parse correctly without throwing errors. Attributes should be allowed on opening tags and self-closing tags.

### System Info
- remark-mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
