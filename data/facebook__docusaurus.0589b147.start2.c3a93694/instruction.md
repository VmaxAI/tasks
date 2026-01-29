# Bug Report

### Describe the bug

I'm encountering an issue with ATX heading parsing where headings are not being recognized correctly. It seems like the parser is immediately exiting the heading token before processing the actual heading content, which causes the heading structure to be malformed.

### Reproduction

```markdown
# Heading 1
## Heading 2
### Heading 3
```

When parsing the above markdown, the headings are not being processed correctly. The parser appears to be exiting the heading state prematurely before it can parse the heading sequence and content.

### Expected behavior

The parser should:
1. Enter the heading state
2. Parse the `#` sequence
3. Parse the heading content
4. Exit the heading state after all content is processed

Instead, it seems to be exiting immediately after entering, which breaks the heading structure.

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: Latest

---
Repository: /testbed
