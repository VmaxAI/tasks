# Bug Report

### Describe the bug

I'm experiencing an issue with slug generation in the docs plugin. When I specify a slug in the frontmatter that starts with a forward slash (`/`), it's being processed incorrectly and the leading slash is being removed.

### Reproduction

Create a markdown file with the following frontmatter:

```md
---
slug: /my-custom-slug
---

# My Document
```

The resulting URL is `/my-custom-slug` without the leading slash being properly handled. It seems like the slug processing logic is now stripping the first character from absolute slugs.

### Expected behavior

When I use `slug: /my-custom-slug` in the frontmatter, it should be treated as an absolute path and used as-is. The leading slash should be preserved and the slug should resolve to the exact path I specified.

Previously this was working correctly - absolute slugs (starting with `/`) were used directly without modification.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
