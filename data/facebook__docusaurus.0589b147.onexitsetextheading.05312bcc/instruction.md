# Bug Report

### Describe the bug

I'm experiencing an issue with setext heading parsing where the internal state management seems broken. After processing setext headings (underlined headings using `===` or `---`), the parser appears to be accessing a property incorrectly, which causes errors when parsing subsequent content.

### Reproduction

```markdown
Heading 1
=========

Some text here

Heading 2
---------

More content
```

When parsing markdown with multiple setext headings, the parser throws an error trying to access properties on the internal data structure. This seems to happen specifically when exiting setext heading nodes.

### Expected behavior

The markdown should parse correctly without errors. Setext headings should be properly processed and the parser state should be cleaned up appropriately after each heading.

### System Info
- remark version: 15.0.1
- Node version: Latest

This appears to be a regression as it was working in previous versions. The issue seems related to how the parser manages internal state when processing setext heading markers.

---
Repository: /testbed
