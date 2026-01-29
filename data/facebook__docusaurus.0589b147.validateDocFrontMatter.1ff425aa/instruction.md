# Bug Report

### Describe the bug

When using custom frontmatter fields in docs, the validation seems to be broken. I'm able to add any arbitrary fields to my markdown files and they're not being validated against the schema anymore. This means invalid or misspelled frontmatter properties are silently accepted instead of throwing validation errors.

### Reproduction

Create a doc file with invalid frontmatter:

```md
---
title: My Doc
invalidField: some value
anotherBadField: 123
---

# Content here
```

### Expected behavior

The build should fail with a validation error indicating that `invalidField` and `anotherBadField` are not valid frontmatter properties for docs. Instead, the build succeeds and these fields are just passed through without any validation.

### System Info
- Docusaurus version: latest
- Node version: 18.x

This seems like a regression - frontmatter validation was working correctly before and catching these types of errors.

---
Repository: /testbed
