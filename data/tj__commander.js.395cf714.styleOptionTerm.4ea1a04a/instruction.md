# Bug Report

### Describe the bug

After a recent update, option names in help output are being displayed in lowercase instead of preserving their original casing. This affects the readability of help text, especially for options that use camelCase or PascalCase naming conventions.

### Reproduction

```js
const program = new Command();
program
  .option('--myOption <value>', 'description for myOption')
  .option('--AnotherFlag', 'description for AnotherFlag');

program.parse();
```

When running with `--help`, the options are now displayed as:
```
--myoption <value>    description for myOption
--anotherflag         description for AnotherFlag
```

### Expected behavior

The option names should preserve their original casing as defined:
```
--myOption <value>    description for myOption
--AnotherFlag         description for AnotherFlag
```

This is particularly problematic for APIs or tools that use specific casing conventions for their option names. The lowercase conversion makes the help text inconsistent with how the options are actually defined and used.

---
Repository: /testbed
