# Bug Report

### Describe the bug

Solidity contract and interface names starting with digits are not being highlighted correctly. When I write a contract name that begins with a number (which is invalid Solidity syntax), the syntax highlighter is incorrectly treating it as a class name instead of ignoring it.

### Reproduction

```solidity
contract 123MyContract {
    // This should not be highlighted as a valid contract name
}

interface 456Interface {
    // This should not be highlighted as a valid interface name
}

struct 789Data {
    // This should not be highlighted as a valid struct name
}
```

All of the above identifiers starting with digits are being highlighted as valid class names, but they shouldn't be since Solidity identifiers cannot start with a digit.

### Expected behavior

Contract, interface, struct, library, and enum names that start with digits should NOT be highlighted as class names, since they are invalid identifiers in Solidity. The syntax highlighter should only match identifiers that follow the valid naming rules (starting with a letter, underscore, or dollar sign).

### System Info
- Using the Solidity language definition for syntax highlighting
- This affects code editors and documentation that rely on this grammar

---
Repository: /testbed
