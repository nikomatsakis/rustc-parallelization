This list comes from reading over Zoxc's commit here:

https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR885

shmut:

- dep-graph
- hir-map (inlined bodies)
- session:
  - lint-store
  - recursion-limit
  - entry-fn etc
  - features
  - etc
  - next-node-id
- caching
  - MIR pred cache
  - trait system:
    - selection cache
  - metadata decoding
- type interning etc
- other:
  - [`derive_macros`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR865)
  - [`stability_interner`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR867)
  - [`interpret_interner`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR869)
  - [`layout_internrer`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR871)
- lazy computation
  - [`all_traits`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR877) (and [this too](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-45ff4c3ed02cc75f5b8162af5d9c782bR705))
- counters
  - layout-depth
- trans back-end
  - [`tx_to_llvm_workers`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR885)
- dep-graph
  - [current diagnostics](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-4f347549534e0019b52bb8603720a445R58)
  - [cnum_map](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-4f347549534e0019b52bb8603720a445R61)
  - [caches lazilly populated during decoding](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-4f347549534e0019b52bb8603720a445R67)
- [MIR stealing](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-aa06547b702d11b0fc84d300a520176fR35)
  - probably best replaced with the linear queries discussed in [#41710](https://github.com/rust-lang/rust/issues/41710)
  - [stuff like this makes me nervous](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-8c516b1674199747f85038166dd95527R131)
- [`record_time`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-ec44cc548fa68e8ba86fe669de5aa7bdR210)
  - used to do little "spot measurements" of execution time for particular things
  - maybe best replaced with `perf` anyway
- [error emitter](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-2c49ea48a32b1e12546e0517e544ef58R265)
- [crate metadata store](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-73ecd822d72423f89997e49c67558804R64)
- [codemap](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c5bde8c46eebaa8f5890c6f3700793b3R127)
- [filemap](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-ec63785db2e65fbfc25c2fe25be8e47cR680)
- [set of active features](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-8821160a043f63ff50982e8b9045ad6dR188)
- [parser session](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-899f995d4388dafbea87f6f67b5c7609R48)
