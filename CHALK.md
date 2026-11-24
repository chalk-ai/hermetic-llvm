# chalk-ai fork of hermetic-llvm

Tags `v<upstream>-chalk.<n>` are upstream releases plus:

- `3rd_party/llvm-project/22.x/patches/thinlto-sorted-distributed-index.patch`: backport of
  llvm/llvm-project df4dc784725a ("[ThinLTO] Write distributed index summaries in GUID order"),
  applied to source-built LLVM 22.x.
- `extensions/llvm_toolchain_minimal_index.json`: LLVM 22.1.8 resolves to `llvm-22.1.8-chalk.1`. Its
  linux-amd64 archive is built from branch `llvm-22.1.8-chalk.1` (upstream `llvm-22.1.8-4` plus the
  patch) with `bazel build --config=release //prebuilt/llvm:for_linux_amd64_musl`. Other platforms use
  upstream's `llvm-22.1.8-4` archives; macOS and Windows builds in chalk-private do not use ThinLTO.

Drop the fork once an upstream release ships an LLVM that contains df4dc784725a.
