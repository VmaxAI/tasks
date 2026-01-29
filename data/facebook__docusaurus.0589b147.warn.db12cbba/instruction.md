# Bug Report

### Describe the bug

When using the logger's `warn()` function with template string interpolation, the values are not being substituted correctly. The logger appears to be treating interpolated strings as plain strings instead of processing the template values.

### Reproduction

```js
import logger from '@docusaurus/logger';

const count = 5;
const type = 'posts';

// This should interpolate the values but doesn't work as expected
logger.warn`Found ${count} ${type} to process`;

// The output shows the raw template instead of "Found 5 posts to process"
```

### Expected behavior

The logger should properly interpolate template string values when using tagged template literal syntax. The variables should be substituted into the message string.

### Additional context

This seems to affect the `warn()` method specifically. Regular string concatenation works fine, but the tagged template literal syntax doesn't process the interpolation values correctly.

---
Repository: /testbed
