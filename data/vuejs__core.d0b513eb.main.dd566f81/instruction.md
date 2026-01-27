# Bug Report

### Describe the bug

The usage size script (`scripts/usage-size.js`) is not generating the complete bundle size report. When running the script to measure bundle sizes for different presets, only one result is being captured instead of all presets.

### Reproduction

Run the usage size script:
```bash
node scripts/usage-size.js
```

Expected: All preset bundles should be processed and their sizes recorded
Actual: Only the first completed bundle is recorded, missing data for other presets

### Additional context

Looking at the output JSON file in `temp/size/_usages.json`, there should be entries for all presets (e.g., `createApp`, `defineComponent`, etc.) but only one entry appears. The file structure also seems incorrect - the keys in the JSON object don't match the expected format.

This is blocking our ability to track bundle size changes across different usage patterns.

---
Repository: /testbed
