# CompatibilityProof

CompatibilityProof is a GenLayer Intelligent Contract for checking whether two products, services, libraries, APIs, standards, or technical systems are compatible using public documentation.

## What it verifies

The user provides:
- a public documentation URL for item A;
- a public documentation URL for item B;
- the names/descriptions of item A and item B;
- one concrete compatibility question.

The contract independently evaluates both sources and returns one of:

- `COMPATIBLE` — the documentation supports compatibility;
- `INCOMPATIBLE` — the documentation shows a material conflict;
- `INSUFFICIENT_DATA` — the available evidence is not enough to decide.

## GenLayer consensus flow

```text
Item A + Source A
        \
         +--> independent web access --> structured LLM decision
        /
Item B + Source B

Leader result
    -> independent validator repeats the analysis
    -> stable decision fields are compared
    -> consensus result
    -> on-chain storage
```

The validator does not require identical evidence wording. It checks the stable decision semantics: the compatibility decision and the per-criterion match states.

## Public methods

- `create_check(source_a_url, source_b_url, item_a, item_b, compatibility_question)` creates a compatibility check.
- `verify_check(check_id)` performs the GenLayer consensus verification.
- `get_check(check_id)` returns the stored record.
- `exists(check_id)` checks whether a record exists.

## Example questions

- Does library A support the runtime/version required by library B?
- Can API A consume the format produced by API B?
- Do product A and accessory B use the same connection standard?
- Does service A meet the authentication/protocol requirements of service B?

## Local validation

Run the same GenLayer environment used for deployment:

```bash
genvm-lint check compatibility_proof.py
genvm-lint schema compatibility_proof.py
```

Deploy the exact `compatibility_proof.py` committed to this repository. The GitHub file, GenLayer Studio deployment, and Explorer address used in the submission should all correspond to this same source.
