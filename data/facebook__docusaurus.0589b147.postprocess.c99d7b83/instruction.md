# Bug Report

### Describe the bug

I'm experiencing an issue with MDX parsing where the event processing seems to be stuck in an infinite loop or producing incorrect results. After some investigation, it appears that the `postprocess` function is behaving unexpectedly when handling event arrays.

### Reproduction

```js
// Parse MDX content with nested structures
const result = await compile('# Hello\n\n**bold** text', {
  // standard MDX options
});
```

When processing certain MDX content, especially with nested inline elements or complex markdown structures, the parser hangs or produces malformed output. The issue seems related to how events are being processed in the tokenization phase.

### Expected behavior

The MDX parser should correctly process all events and return the compiled result without hanging or corrupting the event stream. Events should be processed in their original order without being rearranged.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

---
Repository: /testbed
