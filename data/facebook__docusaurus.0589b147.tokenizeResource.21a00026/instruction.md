# Bug Report

### Describe the bug

I'm encountering an issue with markdown link parsing where links with empty URLs are not being handled correctly. When I try to use a markdown link that has just parentheses with no actual URL, the parser seems to be treating it incorrectly.

### Reproduction

```markdown
[link text]()
```

When parsing the above markdown, the link should be recognized as having an empty destination, but instead it's behaving unexpectedly. It seems like the parser is checking for the wrong character code when determining if the resource section is empty.

### Expected behavior

Links with empty destinations like `[text]()` should be parsed correctly and treated as valid markdown links with an empty URL. The parser should properly recognize when it encounters the closing parenthesis immediately after the opening one.

### Additional context

This appears to affect basic link syntax parsing. I noticed this when trying to create links with empty hrefs that would be filled in dynamically later. The current behavior makes it impossible to use this common markdown pattern.

---
Repository: /testbed
