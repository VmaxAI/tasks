# Bug Report

### Describe the bug

I'm experiencing an issue with blank line parsing in markdown content. It seems like blank lines are not being recognized correctly, which is causing unexpected behavior in the markdown parser.

### Reproduction

When processing markdown with blank lines (lines that contain only whitespace or are completely empty), the parser doesn't handle them properly:

```markdown
Some text here

Another paragraph after a blank line
```

The blank line between the paragraphs should be detected and used to separate them, but instead the parser seems to be treating them incorrectly.

Also noticed issues when there are lines with only spaces:
```markdown
Paragraph 1
    
Paragraph 2
```

### Expected behavior

Blank lines (whether completely empty or containing only whitespace) should be properly tokenized and recognized. This should allow proper separation of markdown elements like paragraphs, lists, etc.

The parser should correctly identify:
- Lines with only spaces/tabs as blank lines
- Completely empty lines as blank lines
- Line endings following blank lines

### System Info
- remark version: 15.0.1

---
Repository: /testbed
