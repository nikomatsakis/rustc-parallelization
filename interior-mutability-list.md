This list comes from reading over Zoxc's commit here:

https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR885

# complete list

- [x] dep-graph
- [x] [hir-map (inlined bodies)](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-2611048bb760f028c808ed4a14b07c00R263)
- [x] [session](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-1c226b200b9385d77428f0b4418366e4R67):
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
- [`record_time`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-ec44cc548fa68e8ba86fe669de5aa7bdR210)
  - used to do little "spot measurements" of execution time for particular things
  - maybe best replaced with `perf` anyway
- [error emitter](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-2c49ea48a32b1e12546e0517e544ef58R265)
- [crate metadata store](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-73ecd822d72423f89997e49c67558804R64)
- [codemap](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c5bde8c46eebaa8f5890c6f3700793b3R127)
- [filemap](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-ec63785db2e65fbfc25c2fe25be8e47cR680)
- [set of active features](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-8821160a043f63ff50982e8b9045ad6dR188)
- [parser session](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-899f995d4388dafbea87f6f67b5c7609R48)

# core structures that will require synchronization

- dep-graph
- [perf-stats](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-1c226b200b9385d77428f0b4418366e4R152)
  - these are just hacky little counters and things
- type interning
  - the global one, anyway -- not sure about inference context?
- [`stability_interner`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR867)
- [`interpret_interner`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR869)
- [`layout_internrer`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR871)
 - [`tx_to_llvm_workers`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR885)
   - this is just a channel, seems fine

# needs to be based on the stack

- layout-depth
  - I think this really wants to walk the stack and count the number of active layout frames, rather than being a counter. Or it could be carried along with the stack. 

# not sure how to handle

- [optimization fuel](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-1c226b200b9385d77428f0b4418366e4R131)
  - this whole premise seems to require a single thread
  - we should just lock to one thread if optimization fuel is given I guess to force deterministic ordering
- 

# things that can be refactored away (and some notes on how)

- hir-map ([inlined bodies](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-2611048bb760f028c808ed4a14b07c00R263))
  - I think that @oli-obk's work on miri makes this go away
- session: (in general, this should go away and become the tcx)
  - buffered-lints
    - iirc, the only reason this exists is because the tcx isn't around to produce the lint-level map query yet
  - recursion-limit
    - move to query
  - entry-fn, plugin crap, etc
    - move to query
  - [crate disambiguator](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-1c226b200b9385d77428f0b4418366e4R93)
    - move to query
  - features
    - move to query
  - etc
- caching
  - MIR pred cache
    - this is linked to a MIR and cleared when it changes. Now that MIR moves linearly through the system, we can recode I suspect to use `&mut` maybe? Or maybe make the computation more explicit (e.g., the cache is populated via explicit action, and then queried, and if it is not populated we get a panic). Synchronization here seems really wasteful in any case.
  - trait system
    - ties in to the WG-traits plans; I would like to completely revamp how trait caching works anyway.
    - but something with locks is prob ok for *now*
- [`all_traits`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR877) (and [this too](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-45ff4c3ed02cc75f5b8162af5d9c782bR705))
  - move to query
- [MIR stealing](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-aa06547b702d11b0fc84d300a520176fR35)
  - probably best replaced with the linear queries discussed in [#41710](https://github.com/rust-lang/rust/issues/41710)
  - [stuff like this makes me nervous](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-8c516b1674199747f85038166dd95527R131)
- [set of active features](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-8821160a043f63ff50982e8b9045ad6dR188)
  - move to query -- come on, are you kidding me??
  
# unclear, would like feedback

- [error emitter](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-2c49ea48a32b1e12546e0517e544ef58R265), [crate metadata store](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-73ecd822d72423f89997e49c67558804R64), [codemap](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c5bde8c46eebaa8f5890c6f3700793b3R127), [filemap](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-ec63785db2e65fbfc25c2fe25be8e47cR680), [parser session](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-899f995d4388dafbea87f6f67b5c7609R48)

  - the main reason they use refcell so extensively is because they are old and mutablity in Rust used to be far easier. But maybe it'd be nice to be able to parse source files in parallel, in which case some amount of synchronization is needed? I'd love to see more of this stuff pushed back into queries though. Thoughts would be welcome here. 
  - cc @petrochenkov, @eddyb, @estebank
- session
  - [lint-store](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-1c226b200b9385d77428f0b4418366e4R78) etc
    - surely this doesn't have to be as wacky as it is
    - cc @manishearth
  - next-node-id
    - no idea what this is all about
- [`derive_macros`](https://github.com/Zoxc/rust/commit/12756affd4ab4467da80ac2e18bde50a8a1c3ede#diff-c8a6d543f758cb294320bcac3b5268aeR865)
  - I have no idea what it is in here really. cc @alexcrichton?
