# Bug Report

### Describe the bug

Links in markdown files are not being transformed/processed anymore. The plugin seems to only handle images now, but regular markdown links are being ignored completely.

### Reproduction

Create a markdown file with a regular link:

```md
[Click here](./some-page.md)
```

The link doesn't get processed/transformed as expected. It seems like the transformer is skipping over link nodes entirely.

### Expected behavior

Both links and images should be processed by the transformer. Regular markdown links should be transformed according to the plugin's configuration (e.g., resolving relative paths, adding base URLs, etc.).

### Additional context

This appears to have started recently. Images might still work, but standard markdown links are definitely not being handled. Not sure if this was an intentional change or a regression.

---
Repository: /testbed
