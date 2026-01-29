# Bug Report

### Describe the bug

After a recent update, MDX link references are not being parsed correctly. When using reference-style links with defined labels, the links are not being recognized and are instead treated as plain text.

### Reproduction

```markdown
Here is a [link reference][my-label].

[my-label]: https://example.com
```

Expected: The link reference should be parsed and rendered as a proper link.

Actual: The link reference is not recognized and appears as plain text in the output.

### Steps to reproduce

1. Create an MDX file with a reference-style link
2. Define the label reference at the bottom of the file
3. Process the MDX file
4. The link is not converted to a proper link element

This seems to affect all reference-style links where the label is defined in the document. Direct links using `[text](url)` syntax still work fine, but the reference syntax is broken.

### System Info
- @mdx-js/mdx version: 3.0.0

---
Repository: /testbed
