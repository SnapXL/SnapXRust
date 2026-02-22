# snapxrust

C# Wrapper for Rust library XCap for macOS. This is an internal component for [SnapX](https://github.com/SnapXL/SnapX).

No support is provided for this library. It is meant for SnapX only.

## Requirements

* Rust toolchain (stable)
* macOS (aarch64 or x86_64)
* .NET 10.0+ (for consumer projects)

## Building

To build the native library:

```bash
cargo build --release
```

To build a universal binary for all macOS architectures:

```bash
rustup target add x86_64-apple-darwin aarch64-apple-darwin
cargo build --release --target x86_64-apple-darwin
cargo build --release --target aarch64-apple-darwin
lipo -create -output libsnapxrust.dylib \
  target/aarch64-apple-darwin/release/libsnapxrust.dylib \
  target/x86_64-apple-darwin/release/libsnapxrust.dylib
```

### Integration

The library is packaged as a NuGet component. It targets the osx runtime identifier. Output binaries are located in runtimes/osx/native.

### License

GPL-3.0-or-later