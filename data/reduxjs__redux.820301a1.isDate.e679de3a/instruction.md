# Bug Report

### Describe the bug

After a recent update, the application crashes immediately when trying to work with Date objects. It appears that date validation/checking functionality has been completely broken.

### Reproduction

```js
import { kindOf } from './utils/kindOf'

const myDate = new Date()
const result = kindOf(myDate)

// Application crashes here - isDate function is missing
```

Any code path that involves checking or validating Date objects will fail. This is affecting:
- Form validation with date inputs
- API responses containing date fields
- Any component that uses date comparison or formatting

### Expected behavior

The `kindOf` utility should properly detect and handle Date objects without crashing. Date validation should work as it did in previous versions.

### System Info
- Version: Latest from main branch
- Node: 18.x

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
