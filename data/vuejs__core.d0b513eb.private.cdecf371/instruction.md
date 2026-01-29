# Bug Report

### Describe the bug

I'm experiencing an issue with template parsing where text content is not being properly emitted in certain scenarios. After parsing a template with text nodes, the text callback doesn't seem to be triggered correctly, resulting in missing content in the parsed output.

### Reproduction

```js
// Parse a template with text content
const template = `<div>Hello World</div>`
const parsed = parse(template)

// The text "Hello World" is not captured correctly
// Expected the text node to be present but it's missing or incomplete
```

This seems to affect templates where text nodes need to be processed during the cleanup phase of tokenization. The issue appears when the tokenizer processes sections of text or RCDATA content.

### Expected behavior

Text content should be properly captured and emitted during template parsing, regardless of when the cleanup occurs. All text nodes should appear in the final parsed result.

### Additional context

This might be related to how the tokenizer handles section boundaries when cleaning up buffered data. The problem seems to occur specifically with text and RCDATA states during the parsing process.

---
Repository: /testbed
