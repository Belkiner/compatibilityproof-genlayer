# AvailabilityConsensus

AvailabilityConsensus is a GenLayer Intelligent Contract that verifies whether a specific product, service, or resource is actually available on a public webpage.

## Why it uses GenLayer

A page can contain ambiguous natural-language availability signals such as "pre-order", "contact us", "sold out", or region-specific conditions. The contract uses GenLayer web access and LLM interpretation, then requires an independent validator to agree on the structured decision.

## Decision model

- `AVAILABLE` — clear evidence that the target can currently be obtained, booked, or ordered.
- `UNAVAILABLE` — clear evidence that the target is unavailable, sold out, discontinued, etc.
- `UNCLEAR` — evidence is insufficient or the target cannot be matched confidently.

The validator compares the stable decision fields rather than requiring identical wording for evidence.

## Contract flow

```text
Target + URL
    -> Web Access
    -> Structured LLM extraction
    -> Independent validator
    -> GenLayer consensus
    -> On-chain result
```

## Public methods

- `create_check(url, target)` creates a verification record.
- `verify_check(check_id)` performs decentralized verification.
- `get_check(check_id)` returns the stored record.
- `exists(check_id)` checks whether a record exists.

## Lint

```bash
genvm-lint check availability_consensus.py
```

> Run the command in a local GenLayer Python environment with the same `py-genlayer` dependency header. The repository was also checked for Python syntax before packaging.
