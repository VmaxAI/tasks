# Bug Report

### Describe the bug

After a recent update, I'm experiencing issues with ES module imports in the browser build. The code seems to be generating incorrect module references that break at runtime.

### Reproduction

When building a Docusaurus project and running it in the browser, I'm getting errors related to module imports. The runtime helpers appear to be using the wrong module format.

Steps to reproduce:
1. Build a Docusaurus project for browser/client-side
2. Check the generated JavaScript output
3. Notice that ES modules are not being used correctly for runtime helpers

The issue seems to be related to how Babel is configured for client vs server builds. The server build works fine, but the browser build is generating code that expects CommonJS modules when it should be using ES modules.

### Expected behavior

The browser build should generate code that uses ES modules (`import`/`export`) for runtime helpers, not CommonJS (`require`). The `useESModules` option should be enabled for client-side builds to ensure compatibility with modern browsers.

### System Info
- Docusaurus version: latest
- Node version: 18.x
- Browser: Chrome/Firefox

---
Repository: /testbed
