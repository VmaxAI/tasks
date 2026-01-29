# Bug Report

### Describe the bug

I'm encountering an issue with autolink parsing in markdown. When I use angle brackets with email addresses or URLs containing dots, the parser seems to be behaving incorrectly. Specifically, autolinks that should be recognized are not being parsed properly.

### Reproduction

```markdown
<user@example.com>
<http://example.com>
<scheme+test://example.com>
```

The autolinks with dots in the scheme/email portion aren't being recognized correctly. It seems like the parser is failing to handle certain character combinations properly, particularly when dots are involved in the scheme or email address validation.

### Expected behavior

All valid autolinks enclosed in angle brackets should be parsed and converted to clickable links. Email addresses and URLs with dots, plus signs, and hyphens in valid positions should be recognized according to the markdown spec.

### Additional context

This appears to affect both email autolinks and URL autolinks. The issue manifests when the autolink contains certain punctuation characters that should be valid according to the autolink syntax rules.

---
Repository: /testbed
