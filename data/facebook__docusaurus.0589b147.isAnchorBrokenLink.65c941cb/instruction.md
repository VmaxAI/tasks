# Bug Report

### Describe the bug

Anchor links on pages are being incorrectly flagged as valid when they should be detected as broken. It seems like the broken link checker is not properly validating anchor links anymore.

### Reproduction

Create a page with the following markdown:

```markdown
# My Page

Some content here.

[Link to non-existent section](#does-not-exist)
```

When building the site, the link `#does-not-exist` should be reported as a broken anchor link since there's no corresponding heading or anchor on the page, but it's not being caught.

### Expected behavior

The broken link checker should detect when an anchor link points to a non-existent section on a page and report it as a broken link. Links like `#does-not-exist` or `/docs/page#missing-section` should be flagged when the target anchor doesn't exist.

### Additional context

This affects the reliability of the broken link detection feature. Pages might be deployed with broken anchor links that users will encounter, even though the build process should have caught them.

---
Repository: /testbed
