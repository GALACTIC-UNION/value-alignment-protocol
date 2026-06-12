# Value Alignment Protocol — Specification

_Version: 0.1.0-draft_

## 1. Scope

This document specifies the normative behavior of the Value Alignment Protocol (VAP) within the OCN.

## 2. Value Representation

All values are expressed in YAML conforming to the schema defined in `config/core-values.yaml`. Each value record contains:

- `id` — unique identifier (e.g., `NHS-001`)
- `label` — human-readable name
- `tier` — `ANCHORED | NEGOTIABLE | CONTEXTUAL`
- `description` — normative prose definition
- `evaluation_method` — reference to the scoring function
- `weight` — float 0.0–1.0 (contribution to composite score)
- `veto_power` — boolean; if true, a score of 0.0 on this value forces overall score to 0.0

## 3. Alignment Score Computation

The composite alignment score S for an entity e is:

```
S(e) = Π(veto values scoring 0) * Σ(weight_i * score_i) / Σ(weight_i)
```

Scores are recomputed on each behavioral observation event and cached in Redis with a 5-minute TTL.

## 4. Negotiation Protocol

_See `docs/negotiation-guide.md` for the full step-by-step process._

## 5. Enforcement

The enforcement module intercepts agent action proposals before execution and computes a projected alignment score delta. If the delta would push the entity below 0.70, the action is blocked and logged.

## 6. Audit & Transparency

All scoring events, proposals, votes, and enforcement blocks are written to an append-only audit log. Quarterly transparency reports are generated from this log.