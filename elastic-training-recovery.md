# Elastic training recovery

## Problem

An interrupted distributed-training service emitted a complete-looking recovery record, but its checkpoint choice, reconstructed tensor state, and resumed training could disagree with the authoritative evidence. The repaired system needed the resumed and uninterrupted paths to reach the same model, optimizer, scheduler, sampler, and random-number state.

## Engineering work

Recovery depends on authenticating content-addressed revisions, selecting a valid checkpoint under explicit rejection precedence, materializing full and sparse-delta state, continuing a deterministic training interval, and repartitioning the final state across an elastic worker topology. The twelve output artifacts form a dependency chain: evidence and lineage establish state; state drives both continuations and rank ownership; reconciliation binds the result.

## Debugging and verification

The difficult failure mode is a plausible checkpoint that passes superficial shape checks but yields a different training continuation or rank partition. Local validation used independently generated expected artifacts, exact state and ownership checks, controlled float tolerances for traces, Oracle and empty controls, and completed wrong-method variants. The later accumulation-focused revision was locally validated, but fresh frontier-model calibration and any platform acceptance are not claimed here.

Protected test fixtures, reference solutions, and answer artifacts are intentionally omitted from this public-facing summary.
