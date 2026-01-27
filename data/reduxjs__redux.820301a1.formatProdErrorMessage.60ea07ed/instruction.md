# Bug Report

### Describe the bug

The production error messages are displaying incorrectly. When an error occurs in production mode, the URL generated for viewing the full error message is malformed and missing the error code parameter value.

### Reproduction

```js
import { formatProdErrorMessage } from 'redux'

// Generate an error message for code 1
const errorMsg = formatProdErrorMessage(1)
console.log(errorMsg)

// Expected output:
// "Minified Redux error #1; visit https://redux.js.org/Errors?code=1 for the full message or use the non-minified dev environment for full errors. "

// Actual output:
// "Minified Redux error #1; visit https://redux.js.org/Errors?code= for the full message or use the non-minified dev environment for full errors. "
```

### Expected behavior

The error message should include the error code in the URL query parameter so users can visit the correct documentation page. Currently the URL ends with `code=` but the actual code number is missing from the query string.

### System Info
- Redux version: latest
- Node version: 18.x

---
Repository: /testbed
