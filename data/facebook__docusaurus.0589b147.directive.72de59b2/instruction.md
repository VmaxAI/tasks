# Bug Report

### Describe the bug

I'm experiencing an issue with directive parsing where text directives are not being recognized properly. It seems like the parser configuration structure has been changed and now text-level directives (using single colon `:`) are not working as expected.

### Reproduction

```markdown
This is a :text-directive[with content] that should be parsed.

Another :directive{key=value} example.
```

When parsing the above markdown with remark-directive, the text directives are not being detected or transformed. The parser seems to skip over them entirely.

### Expected behavior

Text directives should be properly parsed and converted into directive nodes in the AST. The parser should recognize `:directive` syntax at the text level and process them accordingly.

### Additional context

This appears to have started recently. Block-level directives (container `:::` and leaf `::`) might still work, but inline/text directives with single colon are definitely broken.

---
Repository: /testbed
