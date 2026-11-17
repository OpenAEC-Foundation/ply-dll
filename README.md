# ply-dll

Rust PLY mesh reader: ASCII, binary little endian and big endian. The crate is `ply-reader`.

```rust,no_run
let bytes = std::fs::read("model.ply")?;
let geometry = ply_reader::read(&bytes).map_err(std::io::Error::other)?;
# Ok::<(), std::io::Error>(())
```

`read(&[u8])` returns one Mesh. The crate owns its format output types.
Applications convert that output to their own scene representation. This library has no
dependency on a shared application model, loader registry, UI or GPU.

## Validation

`cargo test` runs the self-contained tests. `cargo check --target wasm32-unknown-unknown` checks browser support.

## Current coverage and limitations

ASCII, binary little endian and big endian; optional vertex normals and colours; polygon faces use fan triangulation. Z up. Files without faces are rejected; this is a mesh reader, not a point-cloud reader.

## Use in another application

Add this repository as a Cargo Git dependency pinned to a commit, then call `read`.
These repositories are private; Git requires read access. There are no private dependencies
on other OpenAEC repositories.
