# Bug Report

### Describe the bug

I'm experiencing an issue with the MDX parser where certain markdown features (autolink, indented code blocks, HTML flow, and HTML text) are not being properly disabled. It seems like the configuration for disabling these features isn't taking effect.

### Reproduction

When parsing MDX content that should have these features disabled:

```js
// These markdown features should be disabled but are still being parsed:
// - Autolinks: <http://example.com>
// - Indented code blocks (4 spaces)
// - HTML flow elements
// - Inline HTML text
```

The parser is still processing these elements even though they should be disabled in MDX mode.

### Expected behavior

The specified markdown features (autolink, codeIndented, htmlFlow, htmlText) should be disabled when parsing MDX content, as these features conflict with MDX's JSX syntax.

### System Info
- remark-mdx version: 3.0.0
- micromark-extension-mdx-md: latest

---
Repository: /testbed
