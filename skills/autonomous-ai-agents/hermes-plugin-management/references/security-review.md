# Reviewing Hermes Plugin Security Findings

A plugin can execute code during registration, expose hooks/tools, start MCP or other subprocesses, or inject instructions into agent context. A trust scan is a decision gate, not a cosmetic warning.

## Review procedure

1. Preserve the installer's exact verdict and findings. Do not dismiss a `CAUTION`/`BLOCKED` result based only on the repository's popularity, a clean README, or the user's repository URL.
2. Inspect the plugin manifest and the actual Hermes runtime entrypoint(s), such as `.hermes-plugin/__init__.py`, registered hooks, declared capabilities, subprocess/MCP definitions, dependency manifests, and any scripts invoked during setup or activation.
3. Trace each relevant high-severity finding to its file and determine whether it is executable/runtime behavior or only documentation, tests, examples, or inert strings. A match in documentation may be a false positive, but verify the cited content and check whether the same behavior exists in active code.
4. Decide based on the behavior, not the finding count. If a high-severity concern in executable code remains unexplained, stop and report the blocker. Do not run plugin scripts to "see what happens."
5. Use `--force` only when the user has authorized installation, the runtime code has been reviewed, and the findings that caused the block are demonstrably non-operative or otherwise understood. State that the override bypassed the installer gate.
6. After installation, run `hermes plugins doctor <id>` and inspect enabled status. Doctor's successful import/registration check verifies loading contracts, not that every plugin behavior is benign.

Keep the review scoped to the code and capabilities Hermes will actually load; avoid treating unrelated test fixtures or documentation examples as proof of runtime behavior, while still following any paths they call into.