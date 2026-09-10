# CompatibilityProof

CompatibilityProof verifies whether two products, services, libraries, APIs, standards, or technical systems are compatible for a specific question using two public sources.

## Lifecycle

1. `create_check(...)` creates a `PENDING` record and returns a check ID.
2. `verify_check(check_id)` independently analyzes both sources and reaches validator consensus.
3. The consensus result is stored on-chain in `records`.
4. `get_check(check_id)` returns the stored record.

## Consensus

The leader and validator independently retrieve both sources. Consensus requires agreement on the overall `decision` and the complete normalized criterion vector (`name`, `a`, `b`, `match`). Free-form evidence wording is not used as a consensus key.

## Result

- `COMPATIBLE`
- `INCOMPATIBLE`
- `INSUFFICIENT_DATA`

## Validation

```bash
genvm-lint check compatibility_proof.py
genvm-lint schema compatibility_proof.py
```

Run direct/integration tests before deployment according to the current GenLayer workflow.
