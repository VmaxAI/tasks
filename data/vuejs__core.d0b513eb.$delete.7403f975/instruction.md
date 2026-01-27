# Bug Report

Title: `$delete` method triggers wrong deprecation warning in compat mode

I'm using Vue 3 with the compat build and encountering an issue with the `$delete` method. When I call `this.$delete()` on a component instance, it's showing the wrong deprecation warning.

### Steps to reproduce:
1. Enable compat mode in Vue 3
2. Use `this.$delete(obj, key)` in a component
3. Check the deprecation warning that appears

### Expected behavior
The deprecation warning should indicate that `INSTANCE_DELETE` is being used, since I'm calling `$delete`.

### Actual behavior
The warning shows `INSTANCE_SET` instead, which is confusing because I'm not using `$set` at all. This makes it harder to track down which deprecated APIs are actually being used in the codebase.

### Additional context
This seems like the wrong deprecation type is being checked for the `$delete` method. It's making migration tracking more difficult since the warnings don't match the actual methods being called.

---
Repository: /testbed
