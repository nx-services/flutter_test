# KoreLink Evidence Ledger (tamper-evident twin)

This orphan branch is a git-native mirror of KoreLink's append-only compliance
evidence ledger for this repository. Each commit adds exactly one evidence run:

    records/<head_sha>/<record_id>.json   the canonical record bytes, VERBATIM

To verify independently (KoreLink not required):
  1. For each records file, sha256(file bytes) is the run's record_hash.
  2. Each record's prev_record_hash chains to the previous record (by chain_seq).
  3. The git commit DAG is strictly linear (fast-forward only) — a second,
     independent hash chain over the same bytes.

`index/chain-head` holds the latest "<chain_seq> <record_hash>".
Do not force-push or delete this branch; configure branch protection to block it.
