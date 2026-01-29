# Bug Report

### Describe the bug

The translation keys for blog plugin seem to be incorrect. When trying to customize blog translations, the `sidebar.title` key doesn't work and the descriptions for `title` and `description` fields appear to be swapped.

### Reproduction

In `i18n/en/docusaurus-plugin-content-blog/options.json`:

```json
{
  "title": {
    "message": "My Blog",
    "description": "The title for the blog used in SEO"
  },
  "description": {
    "message": "My blog description",
    "description": "The description for the blog used in SEO"
  },
  "sidebar.title": {
    "message": "Recent posts",
    "description": "The label for the left sidebar"
  }
}
```

The `sidebar.title` key doesn't seem to have any effect on the sidebar label. Also, the descriptions for `title` and `description` fields don't match what they actually control - looks like they might be reversed?

### Expected behavior

- The `sidebar.title` translation key should control the sidebar label
- The description text for each field should accurately describe what it controls

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
