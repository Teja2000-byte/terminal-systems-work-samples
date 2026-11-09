# Repair a conservative flood replay

## Problem

A shallow-water replay could produce plausible trajectories while violating its numerical and conservation contract. The repair had to keep hydraulic state, wet/dry behavior, external forcing, sensor events, and audit outputs consistent across valid input cases.

## Engineering work

The task combines nonuniform terrain, hydrostatic face fluxes, adaptive time steps, friction, revised forcing records, and event ordering. Its connected outputs extend from extracted geometry through the hydraulic replay to conservation and transport-history evidence. The later audit tracks water origin, residence-time moments, first entry into overlapping regions, and attribution of final water to injection cohorts. Those outputs depend on the same accepted hydraulic fluxes; a separate convenient simulation would not satisfy the contract.

## Debugging and verification

The key challenge was distinguishing a numerically plausible run from one that was physically and internally consistent. Validation used fixed synthetic cases with frozen independently generated answers, cross-artifact reconciliation, malformed-input and rollback cases, and separate agent/verifier containers. The reference and an empty/starter control were checked separately; a successful local control was not treated as evidence of model difficulty or platform acceptance.

The full benchmark package, including protected reference answers and hidden cases, is intentionally not published here.
