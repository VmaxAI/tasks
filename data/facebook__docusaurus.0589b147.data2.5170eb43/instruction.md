# Bug Report

### Describe the bug

I'm experiencing an issue with inline code parsing in MDX content. When using backticks for inline code, the parser seems to be consuming characters incorrectly, causing the code text to either terminate prematurely or behave unexpectedly.

### Reproduction

```js
// Example MDX content that triggers the issue
const mdxContent = `
This is some text with \`inline code\` that should work.
`;

// When parsing this content, the inline code is not handled correctly
```

The problem appears when trying to parse inline code blocks (text wrapped in backticks). The parser doesn't seem to properly handle the character consumption within code text data, leading to incorrect tokenization.

### Expected behavior

Inline code wrapped in backticks should be parsed correctly, with all characters between the opening and closing backticks being treated as code text data. The parser should properly iterate through each character and handle the transitions between states.

### System Info
- MDX version: 3.0.0
- Browser/Node: Any

This seems to have started happening recently. The inline code parsing logic might have been modified in a way that breaks the normal flow of character consumption in the tokenizer.

---
Repository: /testbed
