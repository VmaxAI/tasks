# Bug Report

### Describe the bug

I'm experiencing an issue with strikethrough text parsing in markdown. When using the `~~text~~` syntax for strikethrough, the parser seems to be treating it incorrectly or not recognizing it at all in certain contexts.

### Reproduction

```markdown
This is ~~strikethrough text~~ in a paragraph.

Here's another example:
~~deleted content~~
```

When parsing the above markdown, the strikethrough elements are not being processed correctly. The text either doesn't get marked as strikethrough or causes parsing errors.

### Expected behavior

The parser should correctly identify and handle strikethrough syntax (`~~text~~`) and mark the content appropriately. The strikethrough elements should be recognized as valid inline content that can contain end-of-line characters when needed.

### Additional context

This appears to be related to how the GFM (GitHub Flavored Markdown) strikethrough extension is configured. The issue manifests when the markdown contains strikethrough elements, particularly when they span multiple lines or are used in combination with other formatting.

---
Repository: /testbed
