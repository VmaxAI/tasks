# Bug Report

### Describe the bug

I'm encountering an issue with directive container parsing where the closing fence tokens are being created in the wrong order. This causes problems when processing directive containers with closing fences.

### Reproduction

```markdown
:::note
Some content here
:::
```

When parsing the above directive container, the token structure for the closing fence appears to be incorrect. The `directiveContainerFence` and `directiveContainerSequence` tokens are not being entered in the proper order, which breaks the expected token tree structure.

### Expected behavior

The closing fence should properly tokenize with the correct token hierarchy. The `directiveContainerFence` token should be entered before the `directiveContainerSequence` token to match the expected parsing structure.

### Additional context

This affects directive containers that have closing fences (the `:::` at the end). The opening fence seems to work fine, but the closing fence token generation is producing an unexpected structure.

---
Repository: /testbed
