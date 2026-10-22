# Engineering Principles

- Module-specific code lives in the module. Never in core, never in shared helpers.
- Subsystems do not leak into each other. Repositories do not reach into a sibling's internals.
- Two things sharing a pattern get generalized. Applies to code, config, and CI.
- No hacks, no hardcoding, no shortcuts. A shortcut is deferred onto whoever touches it next.
- Never hard-code a list of what the system supports. One canonical list. Every surface reads it.
- These projects are recursive and concurrent. Tests are what keeps that stable. See [testing.md](testing.md).
- Say what you did. Quote real output. The next person searches for the exact string.
