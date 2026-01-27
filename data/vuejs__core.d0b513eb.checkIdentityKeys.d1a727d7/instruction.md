# Bug Report

### Describe the bug

I'm experiencing an issue with reactive Maps and Sets where using reactive objects as keys doesn't trigger the expected identity warning. When I add both a reactive object and its raw counterpart as keys to a reactive Map/Set, I expect to see a warning about having both versions present, but the warning is not being displayed.

### Reproduction

```js
import { reactive } from 'vue'

const map = reactive(new Map())
const key = { id: 1 }
const reactiveKey = reactive(key)

// Add the reactive key
map.set(reactiveKey, 'value1')

// Add the raw key - should warn about having both reactive and raw versions
map.set(key, 'value2')

// Expected: Warning message about containing both raw and reactive versions
// Actual: No warning is shown
```

Same issue occurs with Sets:

```js
const set = reactive(new Set())
const obj = { id: 1 }
const reactiveObj = reactive(obj)

set.add(reactiveObj)
set.add(obj) // Should warn but doesn't
```

### Expected behavior

When a reactive Map or Set contains both a raw object and its reactive version as keys/values, Vue should display a warning to help developers identify potential bugs. This warning used to work correctly but seems to have stopped triggering.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
