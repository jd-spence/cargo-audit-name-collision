# cargo-audit-name-collision
Demonstration of `cargo-audit` auditing crates.io crates instead of in-workspace crates

## Structure
This project contains a placeholder app and a library crate within the workspace named `mock` with version `0.1.0`

## The Issue
Running `cargo audit` in the root of this workspace produces the following output
```
warning: 2 warnings found

Crate:  tempdir
Title:  `tempdir` crate has been deprecated; use `tempfile` instead
Date:   2018-02-13
URL:    https://rustsec.org/advisories/RUSTSEC-2018-0017
Dependency tree:
tempdir 0.3.7
└── cargo-audit-name-collision 0.1.0

Crate:    mock
Version:  0.1.0
Warning:  package has been yanked!
Dependency tree:
mock 0.1.0
└── cargo-audit-name-collision 0.1.0

warning: 2 warnings found!
```

`cargo audit` is finding this yanked [crates.io link](https://crates.io/crates/mock) `mock` crate instead of the in-workspace `mock` crate

It also finding the deprecated crates.io `tempdir` crate instead of the locally defined one that is actually being used