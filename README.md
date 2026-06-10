[update-readmes]   Mode: rewrite — migrating to template structure...
# aarch64-rt

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/aarch64-rt)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/aarch64-rt.git
cd aarch64-rt
```

## Usage


Use the `entry!` macro to mark your main function:

```rust
use aarch64_rt::entry;

entry!(main);
fn main(arg0: u64, arg1: u64, arg2: u64, arg3: u64) -> ! {
    // ...
}
```

`arg0` through `arg3` will contain the initial values of registers `x0`–`x3`. These are often used
to pass arguments from the previous-stage bootloader, such as the address of the device tree.

You'll need to provide the image origin (which will be the entry point address) and maximum size in a linker script, e.g.:

```ld
MEMORY
{
    image : ORIGIN = 0x40080000, LENGTH = 2M
}
```

You'll need to tell Rust to use both this and the `aarch64-rt` linker script in your `build.rs`.
Assuming your linker script is called `memory.ld`:

```rust
fn main() {
    println!("cargo:rustc-link-arg=-Timage.ld");
    println!("cargo:rustc-link-arg=-Tmemory.ld");
    println!("cargo:rerun-if-changed=memory.ld");
}
```

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/aarch64-rt`](https://github.com/Interested-Deving-1896/aarch64-rt) and mirrored through:

```
Interested-Deving-1896/aarch64-rt  ──►  OpenOS-Project-OSP/aarch64-rt  ──►  OpenOS-Project-Ecosystem-OOC/aarch64-rt
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
<!-- License not detected — add a LICENSE file to this repo. -->
<!-- AI:end:license -->
