# Title: ADR-001: Bitflags

## Status: Accepted

## Context

In netlink domain, many properties are expressed as
[bit field][bit_field_wiki], we need to express it in rust native way with
API backwards compatibility.

## Decision

The `bitflags` crate is widely used(e.g. `nix` crate) and API is stable,
hence we decided to use crate [bitflags][bitflags_url] macro to generate bit
field struct instead of human maintained `Vec<FooFlag>`.

## Consequences

### Better

* Less human efforts and typo error

### Worse

The API breakage in `bitflags` will break rust-netlink API backwards
compatibility as the pub struct we expose is created by `bitflags` macros.

The `bitflags` has [bumped its version in 2023][bitflags_api_break]. But the
rust-netlink maintainers agreed to take the risk considering the big benefit
it brings.

[bit_field_wiki]: https://en.wikipedia.org/wiki/Bit_field
[bitflags_url]: https://crates.io/crates/bitflags
[bitflags_api_break]: https://github.com/bitflags/bitflags/releases/tag/2.0.0
