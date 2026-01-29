# Bug Report

### Describe the bug

I'm experiencing an issue where Docusaurus is unable to find my configuration file even though it exists in the site directory. The error message says "No config file found" but my `docusaurus.config.js` is definitely present.

### Reproduction

1. Create a new Docusaurus project with a valid config file (e.g., `docusaurus.config.js`)
2. Try to run any Docusaurus command (build, start, etc.)
3. The command fails with "No config file found" error

The config file is in the root of my site directory and has worked fine in previous versions.

### Expected behavior

Docusaurus should detect and load the configuration file when it exists in the site directory. The build/start commands should proceed normally instead of throwing an error about missing config.

### System Info
- Docusaurus version: latest
- Node version: 18.x
- OS: macOS

Has anyone else run into this? It seems like the config file detection logic might have changed recently.

---
Repository: /testbed
