# Bug Report

### Describe the bug

I'm experiencing an issue with admonition directive parsing in markdown files. It seems like the parser is not correctly handling admonition titles when using the standard three-colon syntax (e.g., `:::note Title`).

### Reproduction

When I have markdown content like this:

```markdown
:::note My Custom Title
This is the content
:::
```

The title parsing doesn't work as expected. The directive label replacement seems to be off or not matching properly.

### Expected behavior

The admonition title should be correctly parsed and converted to the appropriate directive label format. Previously this was working fine with the three-colon syntax for admonitions.

### Additional context

This appears to have started happening recently. I noticed it when updating my documentation - admonitions that were rendering correctly before are now having issues with their titles.

---
Repository: /testbed
