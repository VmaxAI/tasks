# Bug Report

### Describe the bug

I'm experiencing an issue with reactive Map/Set collections where the `delete()` method doesn't seem to be working correctly. After deleting an entry, the reactivity system still triggers updates even though the key no longer exists in the collection.

### Reproduction

```js
const map = reactive(new Map())
const key = { id: 1 }
map.set(key, 'value')

// Delete the entry
map.delete(key)

// The reactivity system behaves unexpectedly here
// It seems like the delete operation is being detected twice or the 
// hadKey check is happening at the wrong time
```

### Expected behavior

When deleting an entry from a reactive Map or Set, the reactivity system should:
1. Check if the key exists BEFORE the deletion
2. Perform the deletion
3. Only trigger updates if the key actually existed

Currently it seems like the existence check might be happening after the deletion completes, which would always return false even when the key was present.

### System Info
- Vue version: 3.x
- Using reactive collections (Map/Set)

---
Repository: /testbed
