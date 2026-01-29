# Bug Report

### Describe the bug

I'm encountering an issue with fenced code blocks in markdown parsing. When using code fences with the same number of backticks/tildes to open and close, the closing fence is not being recognized properly.

### Reproduction

```markdown
~~~
some code
~~~
```

The above code block doesn't close correctly. The closing fence with the same number of characters as the opening fence should work, but it seems like it's being ignored.

### Expected behavior

A fenced code block should be properly closed when the closing fence has the same number of fence characters (backticks or tildes) as the opening fence. According to the CommonMark spec, the closing fence must have at least as many characters as the opening fence.

For example:
- Opening with `~~~` should close with `~~~` or more
- Opening with `` ``` `` should close with `` ``` `` or more

Currently it appears that only closing fences with *more* characters than the opening fence are being recognized, which breaks standard markdown code blocks.

### System Info
- remark version: 15.0.1

---
Repository: /testbed
