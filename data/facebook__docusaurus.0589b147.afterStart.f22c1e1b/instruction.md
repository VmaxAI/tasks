# Bug Report

### Describe the bug

I'm encountering an issue with directive parsing where empty label directives (e.g., `::directive[]`) are not being handled correctly. The parser seems to be entering/exiting token types in the wrong order when processing empty brackets immediately after the opening marker.

### Reproduction

```markdown
::directive[]
```

When parsing this directive with an empty label, the token structure becomes malformed. The issue appears to be related to how the parser handles the case where a closing bracket `]` immediately follows the opening bracket `[` without any content in between.

### Expected behavior

Empty labels should be parsed correctly with proper token entry/exit ordering. The parser should handle `[]` as a valid (though empty) label structure and maintain correct token nesting.

### System Info
- remark-directive version: 3.0.0
- Parser: micromark-based

This seems to have been working in previous versions, so it might be a regression. The token exit/enter sequence appears to be out of order for this edge case.

---
Repository: /testbed
