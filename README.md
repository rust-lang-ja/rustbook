# rustbook [![CircleCI](https://circleci.com/gh/rust-lang-ja/rustbook.svg?style=svg)](https://circleci.com/gh/rust-lang-ja/rustbook)

Build multi-page documentation with Rustdoc.

This is a diverged-fork of
[steveklabnik/rustbook](https://github.com/rust-lang/rust/tree/master/src/tools/rustbook),
and is intended to be the most recent mirror of
[tools/rustbook](https://github.com/rust-lang/rust/tree/master/src/tools/rustbook)
in rust-lang/rust.

**Please note** that the Rust project is
[*moving away from rustbook*](https://github.com/rust-lang/rust/issues/34332).
If you are planning to write a new web book about Rust, it is not
recommended to use rustbook. Please check alternatives such as mdbook
with Rust code snippet support in
[Rust by Example](https://github.com/rust-lang/rust-by-example).


## Installation

### Installing a Nightly Rust via rustup-rs

rustbook requires nightly `rustc` and `rustdoc`. You can use
[rustup-rs](https://github.com/rust-lang-nursery) to install a nightly
version.

First, install `rustup.sh` by following the instructions on
https://www.rustup.rs/

Then, add nightly toolchain.

```
$ rustup install nightly
$ rustup run nightly rustc --version
rustc 1.11.0-nightly (0554abac6 2016-06-10)
```

If you get any errors or questions about rustup-rs, please see
[the Working with Nightly Rust](https://github.com/rust-lang-nursery/rustup.rs#working-with-nightly-rust)
section of rustup-rs README.


### Building and Installing rustbook

Run `cargo install` on the nightly toolchain to download, build and
install rustbook.

```
$ rustup run nightly cargo install --git https://github.com/rust-lang-ja/rustbook.git --branch master
```

### Running rustbook

Unfortunately, rustbook binary is not portable as it has some
dependencies to nightly Rust's dynamic library. You will need to keep
the nightly toolchain installed and run rustbook as the followings:

```
$ rustup run nightly $HOME/.cargo/bin/rustbook
Usage: rustbook <command> [<args>]

The <command> must be one of:
  help    Print this message.
  build   Build the book in subdirectory _book
  serve   --NOT YET IMPLEMENTED--
  test    --NOT YET IMPLEMENTED--
```

You may want to add a command alias to your favorite shell. Please go
ahead and do so.


## Usage

The `rustbook` tool builds a book from a number of separate markdown files. The
contents of the book are determined by a `SUMMARY.md` file like:

```markdown
# Summary

* [Why to use WhizBang](why/README.md)
    * [First reason](why/first.md)
    * [Second reason](why/second.md)
* [How to use WhizBang](how/README.md)
    * [Installing](how/installing.md)
    * [Usage](how/usage.md)
```

The setup is intended to make it easy to browse a book directly on GitHub:

* By convention, each chapter/section with children is placed in its
own subdirectory, with a `README.md` serving as the top level of the
chapter/section.

* Books automatically include an `Introduction` section pointing to the
`README.md` in the root directory.

To build a book, run `rustbook build` in the book's root directory,
which should contain a `SUMMARY.md` and `README.md` as just described.
Currently, the output is always placed in a `_book` subdirectory.


## License

Apache 2.0
