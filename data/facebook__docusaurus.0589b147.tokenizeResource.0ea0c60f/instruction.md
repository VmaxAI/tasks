# Bug Report

### Describe the bug

I'm encountering an issue with markdown link parsing where links with whitespace between the URL and title are not being parsed correctly. The parser seems to be skipping the whitespace handling in certain cases.

### Reproduction

```markdown
[link](url "title")
```

When parsing markdown links that have whitespace between the destination URL and the title, the parser fails to handle the space properly. This affects links with quoted titles that are separated from the URL by spaces or line breaks.

Example that doesn't work as expected:
```markdown
[example](https://example.com "Example Title")
```

The whitespace between `https://example.com` and `"Example Title"` should be consumed before parsing the title, but it appears to be skipped.

### Expected behavior

The parser should correctly handle whitespace between the link destination and title. Links formatted with spaces like `[text](url "title")` should be parsed successfully, with the whitespace properly consumed before the title parsing begins.

### Additional context

This seems to affect standard markdown link syntax where the title is optional and can be separated from the URL by whitespace. The issue appears to be in the resource tokenization logic.

---
Repository: /testbed
