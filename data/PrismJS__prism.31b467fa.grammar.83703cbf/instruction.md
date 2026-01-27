# Bug Report

### Describe the bug

The cooklang syntax highlighting appears to be completely broken. When viewing cooklang recipe files, no syntax highlighting is applied at all - everything shows up as plain text without any color coding or formatting.

### Reproduction

1. Create a file with `.cook` extension
2. Add some cooklang recipe syntax:
```
>> servings: 4

@flour{500%g}
@water{300%ml}
#mixing bowl{}

Mix the @flour and @water in a #bowl for ~{10%minutes}.

-- This is a comment
[- This is also a comment -]
```

3. Open the file in an editor using this grammar

### Expected behavior

The syntax should be highlighted with different colors/styles for:
- Ingredients (starting with `@`)
- Cookware (starting with `#`)
- Timers (starting with `~`)
- Comments (`--` and `[- -]`)
- Metadata lines (`>>`)
- Quantities and units in braces

Instead, everything appears as plain unstyled text with no highlighting at all.

### Additional context

This seems to have broken recently - the grammar definition appears to be incomplete or truncated. The highlighting was working fine before.

---
Repository: /testbed
