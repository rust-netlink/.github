# Title: ADR-002: Non-Linux Support

## Status: Accepted

## Context

We see rust-netlink crates been used in non-linux platform, but developer
are assuming the code is running on linux OS as userspace tool.
This assumption will break non-linux use cases.

## Decision

Developer of rust-netlink should coding with non-linux use case in mind,
including but not limited to:
 * CI test case for compiling on non-linux target.
 * Do not use panic-able syntax(e.g. `slice[index]`) even that is hard coded
   in linux kernel.
 * The data passing to rust-netlink crates might coming from user, not just
   from realizable source like kernel.

## Consequences

### Better

More user, more test, less bug.

### Worse

More human efforts.
