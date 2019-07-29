# AutoArgs [![Build Status](https://travis-ci.org/droundy/auto_args.svg?branch=master)](https://travis-ci.org/droundy/auto_args) [![](https://img.shields.io/crates/v/auto_args.svg)](https://crates.io/crates/auto_args) [![](https://docs.rs/auto_args/badge.svg)](https://docs.rs/auto_args)

Parse command line arguments by defining a struct.  It combines
[clap](https://crates.io/crates/clap) with custom derive.

The basic idea is that you define a type that represents the
information you want on the command-line from the person running your
program, and `derive(AutoArgs)` on that type, and then call
`YourType::from_args()` to find out what your user gave you.

## Relationship to clap

AutoArgs uses [clap](https://clap.rs) to do the actual parsing of
command-line flags.  This is great, because clap does an awesome job
at providing helpful features you wouldn't even have thought of if you
wrote your own command-line processor.  The biggest downside to using
clap directly is that it does not nicely support translating its
results into something you would want to use in your code, so there is
a fair amount of repetitious calling of macros to do conversions into
useful types.

## Differences from structopt

[StructOpt](https://docs.rs/structopt) is a tool that serves the same
function as `auto_args`, but with a different philosophy.  StructOpt
strives to be as expressive as clap, and to enable all features clap
does, and with a tightly coupled API.  It does this by extensive use
of attributes such as `#[structopt(long = "long-name")]`, which define
the behavior and property of each flag.  This makes it powerful, but
also rather verbose to use.

In contrast, AutoArgs does not (yet?) support any attributes, and
determines all behavior directly from your type.  This means that you
don't repeat yourself, but also means that you have less fine-grained
control over your interface, and some interfaces may be well-nigh
impossible.

You *can* implement the `AutoArgs` trait manually, which does make it
possible (and not even that painful) to create a different
command-line for a given type, but this is not the intended way to use
`AutoArgs`.

## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or
  <https://www.apache.org/licenses/LICENSE-2.0>)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or
  <https://opensource.org/licenses/MIT>)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally
submitted for inclusion in the work by you, as defined in the
Apache-2.0 license, shall be dual licensed as above, without any
additional terms or conditions.
