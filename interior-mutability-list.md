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
  - [`all_traits`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR877)
- counters
  - layout-depth
- trans back-end
  - [`tx_to_llvm_workers`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR885)
-
