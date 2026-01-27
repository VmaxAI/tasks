# Bug Report

### Describe the bug

I'm encountering an issue with CDATA section parsing in the template compiler. When a CDATA section is present in the template, the content appears to be incorrectly extracted - it seems like the first character of the CDATA content is being cut off or the parsing is starting at the wrong position.

### Reproduction

```js
const template = `<div><![CDATA[Hello World]]></div>`

// After parsing, the CDATA content should be "Hello World"
// But it appears to be missing the first character or offset incorrectly
```

This seems to affect templates that include CDATA sections, which are sometimes used when embedding XML or special content within templates.

### Expected behavior

The CDATA section content should be parsed completely and accurately, with all characters preserved from the original source.

### Additional context

This appears to be related to how the tokenizer handles the transition from detecting the CDATA sequence to actually reading the CDATA content. The boundary between these states might not be calculated correctly.

---
Repository: /testbed
