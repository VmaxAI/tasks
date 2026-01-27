# Bug Report

### Describe the bug

I'm experiencing issues with Map operations after a recent update. The Map draft implementation seems to be incomplete or corrupted - methods like `get`, `set`, `delete`, `clear`, and iteration methods are not working properly.

### Reproduction

```js
import {produce} from 'immer'

const state = {
  myMap: new Map([
    ['key1', 'value1'],
    ['key2', 'value2']
  ])
}

const nextState = produce(state, draft => {
  // Trying to set a new value
  draft.myMap.set('key3', 'value3')
  
  // Trying to get a value
  const val = draft.myMap.get('key1')
  console.log(val) // Expected: 'value1', but getting errors
  
  // Trying to delete a key
  draft.myMap.delete('key2')
})
```

When I try to perform any Map operations on a draft, I'm getting errors or undefined behavior. It seems like the Map proxy methods are missing or incomplete.

### Expected behavior

Map operations should work normally on draft Maps:
- `set()` should add/update entries
- `get()` should retrieve values
- `delete()` should remove entries
- `clear()` should empty the Map
- Iteration methods (`keys()`, `values()`, `forEach()`) should work as expected

### Additional context

This appears to have broken recently. The DraftMap class seems to be missing its method implementations. Not sure if this was an incomplete refactoring or if something went wrong during a merge.

---
Repository: /testbed
