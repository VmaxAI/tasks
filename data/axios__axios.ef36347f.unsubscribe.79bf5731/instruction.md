# Bug Report

### Describe the bug

I'm experiencing an issue with signal composition where the `unsubscribe` method is being called immediately instead of being deferred. This causes the signal to be unsubscribed right away when creating a composed signal, rather than waiting until `signal.unsubscribe()` is actually invoked.

### Reproduction

```js
const controller = new AbortController();
const signals = [controller.signal];

const composedSignal = composeSignals(signals, 5000);

// At this point, the unsubscribe has already been called
// even though we haven't called composedSignal.unsubscribe() yet

// Later when we try to unsubscribe:
composedSignal.unsubscribe(); // This doesn't work as expected
```

### Expected behavior

The `unsubscribe` function should only be executed when `signal.unsubscribe()` is called, not during the signal composition setup. The unsubscribe callback should be deferred until the user explicitly calls it.

### Additional context

This appears to have broken after a recent change. The unsubscribe logic is being invoked too early, which means any cleanup or event listener removal happens before it should.

---
Repository: /testbed
