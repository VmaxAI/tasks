# Bug Report

### Describe the bug

Text directives are not being recognized in markdown content. When trying to use inline directives with the `:` syntax, they don't get parsed correctly and appear as plain text instead.

### Reproduction

```markdown
This is a :textdirective[with content] that should be parsed.

Another example: :inline[directive]{key=value}
```

The text directives above are not being processed and remain as literal text in the output.

### Expected behavior

Text directives starting with `:` followed by the directive name should be parsed and converted into directive nodes in the AST. The parser should recognize these as valid directive syntax.

### Additional context

Container and leaf directives seem to work fine with `::` and `:::` syntax, but single-colon text directives are not being detected. This affects any markdown content that relies on inline directive syntax.

---
Repository: /testbed
