# Bug Report

### Describe the bug

When using front matter with numeric values in Docusaurus, the values are not being converted to strings as expected. This causes validation issues when the schema expects string types but receives numbers.

### Reproduction

```yaml
---
title: My Page
version: 1.5
port: 8080
---
```

When processing this front matter, numeric values like `version` and `port` should be automatically converted to strings if the schema expects strings, but they remain as numbers instead.

### Expected behavior

Numeric values in front matter should be automatically converted to strings when needed, similar to how YAML parsers handle type coercion. The `version: 1.5` should become `"1.5"` and `port: 8080` should become `"8080"` when the validation schema expects string types.

### System Info
- Docusaurus version: latest
- Node version: 18.x

This is blocking our migration since we have many existing markdown files with numeric values in front matter that need to be treated as strings.

---
Repository: /testbed
