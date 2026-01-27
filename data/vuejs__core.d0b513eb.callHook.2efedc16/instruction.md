# Bug Report

### Describe the bug

I'm experiencing an issue with transitions where the `onAfterEnter` hook is being called even when the enter transition is cancelled. According to the documentation, the after hook should only fire when the transition completes successfully, not when it's interrupted.

### Reproduction

```js
<Transition
  @after-enter="onAfterEnter"
  @enter-cancelled="onEnterCancelled"
>
  <div v-if="show">Content</div>
</Transition>

// Quickly toggle show to cancel the enter transition
show = true
setTimeout(() => show = false, 50) // Cancel before transition completes

// Expected: only onEnterCancelled fires
// Actual: both onEnterCancelled AND onAfterEnter fire
```

### Expected behavior

When an enter transition is cancelled, only the `onEnterCancelled` hook should be called. The `onAfterEnter` hook should not fire since the transition did not complete successfully.

### System Info
- Vue version: 3.x
- Browser: Chrome/Firefox

This seems like a regression as I don't remember this happening in earlier versions. The after hook firing on cancellation is causing issues in my app where I'm performing cleanup operations that should only happen on successful transitions.

---
Repository: /testbed
