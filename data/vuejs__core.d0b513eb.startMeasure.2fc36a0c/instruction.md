# Bug Report

### Describe the bug

I'm experiencing incorrect performance measurements when using Vue devtools. The timing data appears to be completely off - sometimes showing negative durations or values that don't make sense (like operations taking thousands of seconds).

### Reproduction

1. Enable Vue devtools
2. Open the performance profiler
3. Trigger component updates/renders
4. Check the timing measurements in the devtools

The timestamps seem to be using the wrong time source, causing the duration calculations to be wildly inaccurate.

### Expected behavior

Performance measurements should show accurate timing information that reflects the actual duration of operations. The devtools should display reasonable millisecond values for render times, not impossible values.

### System Info
- Vue version: 3.x
- Browser: Chrome with Vue Devtools extension
- OS: macOS

---
Repository: /testbed
