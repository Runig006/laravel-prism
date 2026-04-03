# Prism — Patched

## clientExecuted: skip tool execution
Tools are always marked as `clientExecuted` — Prism sends tool definitions to the LLM
but never executes them. The caller handles execution externally.

- `src/Tool.php` — added `$clientExecuted` property, `clientExecuted()` setter, `isClientExecuted()` getter
- `src/Text/PendingRequest.php` — `toRequest()` marks all tools as `clientExecuted()`
- `src/Concerns/CallsTools.php` — `callTools()` returns `[]` when first tool is `clientExecuted`
