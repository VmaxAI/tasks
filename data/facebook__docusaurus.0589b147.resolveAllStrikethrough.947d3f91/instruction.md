# Bug Report

### Describe the bug

I'm experiencing an issue with strikethrough parsing in markdown text. When I try to use strikethrough syntax (`~~text~~`), it's not being rendered correctly. The text either appears without strikethrough formatting or the tildes are shown as literal characters.

### Reproduction

```markdown
This is ~~strikethrough text~~ that should be crossed out.

Also trying ~~multiple~~ ~~strikethroughs~~ in the same line.
```

Expected the strikethrough to be applied, but the text renders without any formatting or with the `~~` characters visible.

### Expected behavior

The text between `~~` markers should be rendered with strikethrough formatting applied. Multiple strikethroughs in the same content should all work correctly.

### Additional context

This seems to have started happening recently. Regular markdown formatting like bold and italics works fine, but strikethrough specifically is broken. I'm using GFM (GitHub Flavored Markdown) syntax which should support strikethrough out of the box.

---
Repository: /testbed
