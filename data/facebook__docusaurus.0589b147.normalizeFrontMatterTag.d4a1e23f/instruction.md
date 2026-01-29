# Bug Report

### Describe the bug

When using tags in front matter, the tag permalinks are being generated incorrectly. It looks like the permalink is now including the full tags path twice, resulting in malformed URLs like `/tags/tags/my-tag` instead of the expected `/tags/my-tag`.

### Reproduction

```yaml
---
tags:
  - my-tag
  - another-tag
---
```

When you define tags in the front matter like above, the generated permalinks end up being doubled. For example, if your `tagsPath` is `/tags`, clicking on a tag leads to `/tags/tags/my-tag` instead of `/tags/my-tag`.

This seems to have started happening recently. Previously, the tag permalinks were working fine and generated correct paths.

### Expected behavior

Tag permalinks should be generated as `/tags/my-tag` (or whatever your configured tags path is), not `/tags/tags/my-tag`.

### Additional context

This affects all tag links throughout the site - both in the front matter tags and anywhere else tags are displayed and linked.

---
Repository: /testbed
