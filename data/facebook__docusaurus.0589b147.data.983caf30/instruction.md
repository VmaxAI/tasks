# Bug Report

### Describe the bug

I'm encountering an issue with markdown parsing where text containing certain break characters is being consumed twice, resulting in corrupted output or unexpected behavior when processing markdown content.

### Reproduction

```js
const markdown = `Some text with line breaks

Another paragraph here`

// Parse the markdown
const result = parseMarkdown(markdown)

// The output is malformed - break characters appear to be duplicated or processed incorrectly
```

### Expected behavior

The markdown parser should correctly handle break characters in text data without consuming them multiple times. Each character should be processed exactly once during the parsing flow.

### System Info
- remark version: 15.0.1
- Node version: Latest

This seems to have started recently and is affecting markdown documents with line breaks between paragraphs. The parsed output doesn't match what we'd expect from the input.

---
Repository: /testbed
