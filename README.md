# cargo-audit-name-collision
Demonstration of `cargo-audit` auditing crates.io crates instead of in-workspace crates

## Structure
This project contains a placeholder app and a library crate within the workspace named `mock` with version `0.1.0`

## The Issue
Running `cargo audit` in the root of this workspace produces the following output
```
warning: 1 warning found

Crate:    mock
Version:  0.1.0
Warning:  package has been yanked!
Dependency tree:
mock 0.1.0
└── cargo-audit-name-collision 0.1.0

warning: 1 warning found!
```

`cargo audit` is finding this [crates.io link](https://crates.io/crates/mock) `mock` crate instead of the in-workspace `mock` crate