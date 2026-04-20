# CLAUDE.md — Project-Substrate/memgraph

Magnon fork of Memgraph — in-memory graph database used by Substrate for topology storage, dependency graphs, and the Magnon knowledge graph.

## Upstream

`upstream` → `https://github.com/memgraph/memgraph.git`

Pull upstream changes: `git fetch upstream && git merge upstream/master`

## Magnon Customisations

- Custom query modules for Magnon topology queries (node/edge types, Substrate-specific traversals)
- Build configuration adjusted for Hetzner ARM/x86 nodes
- Integration with OTel tracing for query observability

## Key Commands

```bash
# Build
./build.sh

# Run tests
ctest --test-dir build
```

## Key Invariants

- Custom query modules live in `magnon/` — keep them separate from upstream code.
- Upstream Memgraph releases are large C++ builds — merge upstream carefully and run the full test suite before deploying.
- Memgraph stores the Substrate topology graph consumed by `Project-Substrate/magic` — schema changes require coordination with the Magic team.
