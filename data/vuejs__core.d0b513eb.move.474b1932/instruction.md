# Bug Report

### Describe the bug

I'm encountering an issue with `Suspense` components when they are being moved/teleported in the DOM. The component seems to be using stale container references during the move operation, which can cause the active branch to be moved to the wrong container.

### Reproduction

```js
const app = createApp({
  template: `
    <Teleport :to="target">
      <Suspense>
        <template #default>
          <AsyncComponent />
        </template>
      </Suspense>
    </Teleport>
  `
})

// When the teleport target changes, the Suspense's active branch
// gets moved but uses the old container reference instead of the new one
```

### Expected behavior

When a Suspense component is moved to a new container (e.g., via Teleport), its active branch should be moved to the new container, not the old one. The container reference should be updated before attempting to move the active branch.

### System Info
- Vue version: 3.x
- Runtime: Browser

---
Repository: /testbed
