# Bug Report

### Describe the bug

After a recent update, the broken links checker seems to be behaving incorrectly. Links that should be detected as valid are now being flagged as broken, and anchor links are not being processed properly.

### Reproduction

I have a site with the following structure:

```md
<!-- page1.md -->
# Page 1
[Link to page 2](./page2.md)
[Anchor link](#section)

## Section
Content here
```

```md
<!-- page2.md -->
# Page 2
Content
```

When building the site, I'm seeing unexpected broken link warnings for what appear to be valid internal links. The links work fine when navigating the site, but the build process reports them as broken.

### Expected behavior

Valid internal links should not be flagged as broken during the build process. Anchor links should be correctly identified and validated.

### System Info

- Docusaurus version: latest
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
