# Bug Report

### Describe the bug

The application crashes on startup with a syntax error. It appears that some Python code was accidentally inserted into a JavaScript file, breaking the entire module.

### Reproduction

1. Start the application
2. The process immediately fails with a parsing error

The error occurs in `lib/command.js` where there's invalid JavaScript syntax. It looks like code from a completely different language (Python) got mixed into the JavaScript source file, specifically in the `_outputConfiguration` object definition.

### Expected behavior

The application should start normally without any syntax errors. The `_outputConfiguration` object should be properly defined with valid JavaScript code.

### System Info
- Node.js version: (any)
- OS: (any)

This is blocking all functionality since the module can't even be loaded. The file needs to have the correct JavaScript syntax restored.

---
Repository: /testbed
