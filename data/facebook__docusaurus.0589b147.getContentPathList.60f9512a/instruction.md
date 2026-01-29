# Bug Report

### Describe the bug

When using the pages plugin, content from the base `contentPath` directory is no longer being loaded. Only localized content from `contentPathLocalized` is being picked up, which means pages that exist in the base content directory are not being discovered or rendered.

### Reproduction

1. Create a Docusaurus site with the pages plugin configured
2. Add a page file (e.g., `my-page.md`) to the base pages directory (typically `src/pages`)
3. Add a localized version to the localized directory (e.g., `i18n/en/docusaurus-plugin-content-pages/my-other-page.md`)
4. Build or start the dev server

**Expected behavior:**
Both the base page and the localized page should be available and rendered.

**Actual behavior:**
Only the localized page is found. The page in the base `src/pages` directory is not being loaded.

### System Info
- Docusaurus version: latest
- Node version: 18.x

This seems to have broken after a recent update. Previously, pages from both directories were working correctly.

---
Repository: /testbed
