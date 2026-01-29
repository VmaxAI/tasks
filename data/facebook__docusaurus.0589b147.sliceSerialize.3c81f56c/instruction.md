# Bug Report

### Describe the bug

I'm encountering an issue with markdown parsing where the serialization of tokens appears to be producing incorrect output. The text content isn't being extracted properly from the token stream.

### Reproduction

When parsing markdown content with certain structures, the serialized output doesn't match the expected text. For example:

```js
const markdown = `
# Heading
Some text with **bold** content
`;

// Parse the markdown
const tree = parse(markdown);
// Serialize tokens
const serialized = sliceSerialize(token, true);

// The output is not the expected string representation
```

### Expected behavior

The `sliceSerialize` function should correctly extract and return the string content from the token stream, with tabs expanded if requested. Currently it seems like the order of operations is wrong and the output isn't a proper string.

### System Info
- remark version: 15.0.1
- Node version: 18.x

---
Repository: /testbed
