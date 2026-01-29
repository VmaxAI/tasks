# Bug Report

### Describe the bug

After a recent update, I'm experiencing issues with feature flags not being properly initialized in certain build environments. The application seems to be initializing feature flags in scenarios where they shouldn't be, causing unexpected behavior in production builds.

### Reproduction

This is affecting ESM bundler builds specifically. The issue appears when:

1. Using an ESM bundler configuration
2. Running in a production environment
3. Feature flags are being initialized when they should be skipped

The problem manifests as feature flags being incorrectly initialized, which can lead to:
- Unexpected runtime behavior
- Performance degradation
- Inconsistent feature availability across different build targets

### Expected behavior

Feature flags should only be initialized under the correct conditions based on the build environment. In ESM bundler builds with test mode disabled, the initialization logic should work as intended without incorrectly triggering in production scenarios.

### System Info
- Vue version: 3.x
- Build tool: ESM bundler
- Environment: Production

---
Repository: /testbed
