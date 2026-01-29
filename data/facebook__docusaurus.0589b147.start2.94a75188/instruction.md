# Bug Report

### Describe the bug

I'm encountering an issue with link parsing in MDX content. When using standard markdown links, the parser seems to be incorrectly handling the label markers, which causes the link structure to be malformed.

### Reproduction

```markdown
This is a [test link](https://example.com) in my document.
```

When parsing the above MDX content, the link label tokens appear to be nested incorrectly. The parser enters `labelMarker` twice but exits them in the wrong order, leading to an imbalanced token tree.

### Expected behavior

Links should be parsed correctly with properly balanced enter/exit calls for each token type. The token structure should follow the pattern:
1. Enter labelLink
2. Enter labelMarker
3. Consume character
4. Exit labelMarker
5. Exit labelLink

### System Info
- @mdx-js/mdx version: 3.0.0
- Node version: 18.x

This seems to have started happening recently. Any help would be appreciated!

---
Repository: /testbed
