# Bug Report

### Describe the bug

Fenced code blocks with exactly 3 backticks or tildes are not being recognized as valid code fences. The parser seems to require more than 3 fence characters, but according to the CommonMark spec, 3 characters should be the minimum valid fence length.

### Reproduction

```markdown
```javascript
console.log('hello');
```
```

The above code block with exactly 3 backticks is not being parsed correctly. It should be recognized as a valid fenced code block, but it's being treated as something else.

Same issue occurs with tildes:

```markdown
~~~
some code
~~~
```

### Expected behavior

According to the CommonMark specification, a code fence must consist of at least 3 consecutive backtick or tilde characters. The parser should accept fenced code blocks that use exactly 3 fence characters (the minimum), not require more than 3.

Both of the examples above should be parsed as valid fenced code blocks.

### System Info
- remark version: 15.0.1

---
Repository: /testbed
