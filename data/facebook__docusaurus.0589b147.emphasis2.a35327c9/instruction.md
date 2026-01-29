# Bug Report

### Describe the bug

I'm experiencing an issue with markdown emphasis rendering. When using single asterisks or underscores for emphasis (italic text), the output is being rendered as strong/bold instead.

### Reproduction

```js
const markdown = '*this should be italic*';
// or
const markdown = '_this should also be italic_';
```

When processing this markdown, the text is being rendered as bold/strong instead of emphasized/italic.

### Expected behavior

Single asterisks or underscores should create `<em>` tags (italic text), not `<strong>` tags (bold text). Double asterisks/underscores should be used for bold.

According to markdown spec:
- `*text*` or `_text_` → italic/emphasis
- `**text**` or `__text__` → bold/strong

### System Info
- remark version: 15.0.1

---
Repository: /testbed
