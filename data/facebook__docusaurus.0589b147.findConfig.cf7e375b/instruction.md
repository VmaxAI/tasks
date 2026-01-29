# Bug Report

### Describe the bug

After a recent update, Docusaurus is not loading my config file anymore. The build process fails immediately with an error saying "No config file found" even though I have a valid `docusaurus.config.js` file in my project root.

### Reproduction

1. Create a new Docusaurus project or use an existing one
2. Make sure you have a `docusaurus.config.js` (or `.ts`, `.mjs`, etc.) in the site directory
3. Run the build or start command
4. The process fails with "No config file found" error

### Expected behavior

Docusaurus should detect and load the config file normally. The config file is present and valid, so the build should proceed without errors.

### Additional context

This worked fine in the previous version. The config file hasn't been moved or renamed. It seems like the config detection logic might be inverted somehow - it's throwing an error when it *finds* the config instead of when it *doesn't find* it.

---
Repository: /testbed
