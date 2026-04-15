# Elementary
## "Elementary, ny dear Watson" Sherlock Holmes

A terminal-based interactive downloader for Windows forensics, sysadmin, and security tools — written in Rust.

## Features

- Fully interactive TUI (keyboard-driven, no mouse needed)
- Organised into tool categories with multi-select
- Downloads directly to `~/Downloads/elementary/`



## Build

Requirements: [Rust toolchain](https://rustup.rs/) (stable, 1.75+)

```bash
cd toolkit-dl
cargo build --release
```

Binary will be at `target/release/elementary.exe` 

## Run

```bash
cargo run --release
# or directly:
./target/release/elementary
```

## Adding Your Own Tools

Edit the `catalogue()` function in `src/main.rs`. Each tool is a simple struct:

```rust
Tool {
    name: "My Tool",
    description: "What it does",
    url: "https://example.com/mytool.zip",
    filename: "mytool.zip",
},
```

Add it to the relevant `ToolCategory`, or create a new one.

## Notes

- This tool downloads Windows executables. Running it on Linux/macOS will work but the downloaded files are Windows-only.
- Some tools (Mimikatz, credential tools) may trigger AV — add exceptions as needed for your forensics environment.
- No tool is bundled — all downloads happen at runtime from official/GitHub sources.
