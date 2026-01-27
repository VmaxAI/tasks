# Bug Report

### Describe the bug

The Latte language syntax highlighting is broken. When trying to use the latte language, the code appears to be incomplete or malformed, causing issues with tokenization.

### Reproduction

```js
import { highlightCode } from 'prismjs';

const latteCode = `
{if $user}
  <div n:attr="class => $class">
    {$user->name}
  </div>
{/if}
`;

// Attempting to highlight latte code fails
const result = highlightCode(latteCode, 'latte');
```

### Expected behavior

The Latte code should be properly highlighted with:
- Latte comments (`{* ... *}`) recognized
- Latte tags (`{if}`, `{/if}`, etc.) properly tokenized
- n:attr attributes in HTML tags highlighted correctly
- Embedded PHP expressions working inside latte tags

### System Info
- Latest version from main branch
- The latte grammar definition seems to be cut off or incomplete

---
Repository: /testbed
