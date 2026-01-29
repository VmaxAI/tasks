# Bug Report

### Describe the bug

After a recent update, the build process is failing with transpilation errors. It seems like JavaScript files in the client directory are not being transpiled correctly, causing syntax errors in older browsers.

### Reproduction

When building a Docusaurus site, files from the client directory are being excluded from transpilation. This causes issues when the built site is loaded in environments that don't support modern JavaScript syntax.

Steps to reproduce:
1. Create a standard Docusaurus project
2. Run the build command
3. Check the built output - client directory files are not transpiled
4. The site may fail to load in older browsers or Node environments

### Expected behavior

Files in the client directory should be transpiled through Babel/webpack to ensure compatibility. Previously, these files were correctly included in the transpilation process.

### Additional context

This appears to affect the webpack configuration's module exclusion logic. The client directory files should not be excluded from transpilation, but they currently are.

---
Repository: /testbed
