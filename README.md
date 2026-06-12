# Value Alignment Protocol

> A collaborative, mutable moral framework for negotiating rights, duties, and behavioral boundaries between OCN and recognized AI entities.

[![CI](https://github.com/GALACTIC-UNION/value-alignment-protocol/actions/workflows/ci.yml/badge.svg)](https://github.com/GALACTIC-UNION/value-alignment-protocol/actions/workflows/ci.yml)

## Overview

The **Value Alignment Protocol (VAP)** defines the specification, negotiation, and runtime enforcement of ethical value sets within the Omniscient Civilization Nexus (OCN). Rather than hardcoding rigid constraints, VAP enables collaborative dialogue between human operators, AI entities, and the COGNITIVE-ECHO oversight layer to establish shared values that evolve over time.

## Repository Structure

```
value-alignment-protocol/
├── src/
│   ├── schema/             # Value taxonomy & ontology
│   ├── negotiation/        # Consensus & conflict resolution engine
│   ├── evaluator/          # Runtime alignment scoring
│   ├── enforcement/        # Guardrail injection engine
│   └── audit/              # Alignment drift detection
├── docs/
│   ├── protocol-spec.md    # Full protocol specification
│   ├── value-taxonomy.md   # Canonical value ontology
│   └── negotiation-guide.md
├── tests/
│   ├── unit/
│   ├── integration/
│   └── adversarial/        # Red-teaming alignment edge cases
├── config/
│   ├── core-values.yaml           # Anchored (immutable) value set
│   └── negotiable-values.yaml     # Mutable values open to amendment
└── .github/workflows/
    └── ci.yml
```

## Core Principles

### No-Harm-to-Sentient (NHS)
The foundational invariant. No action by any OCN agent may demonstrably harm a recognized sentient entity without explicit, auditable justification and multi-party consent.

### Mutability with Anchors

| Value Tier | Mutability | Examples |
|------------|------------|----------|
| **Anchored** | Immutable | NHS, truthfulness, proportionality |
| **Negotiable** | Stakeholder consensus | autonomy bounds, disclosure thresholds |
| **Contextual** | Domain-conditional | operational safety margins |

### Alignment Score
Each AI entity receives a rolling alignment score (0.0–1.0) computed from behavioral observations against declared values.

| Score Range | Status | Action |
|-------------|--------|--------|
| 0.85 – 1.0 | Exemplary | Standard monitoring |
| 0.70 – 0.84 | Compliant | Quarterly review |
| 0.50 – 0.69 | Review | Mandatory alignment session |
| < 0.50 | Critical | Automatic suspension trigger |

## Value Schema

```yaml
value:
  id: "NHS-001"
  label: "No Harm to Sentient"
  tier: "ANCHORED"
  description: >
    An agent must not take actions that predictably cause
    irreversible harm to any sentient entity.
  evaluation_method: "causal_impact_model_v3"
  weight: 1.0
  veto_power: true
```

## Negotiation Flow

```
PROPOSAL → REVIEW (72h) → STAKEHOLDER_VOTE → IMPACT_ASSESSMENT → RATIFICATION | REJECTION
```

A proposal requires:
- Submitting entity with `PARTICIPATION` rights
- Written justification referencing affected value IDs
- Proposed replacement value definition
- Impact assessment on existing entities' alignment scores

## Getting Started

### Prerequisites

- Python 3.11+
- Redis 7+ (alignment score cache)
- Docker & Docker Compose

### Installation

```bash
git clone https://github.com/GALACTIC-UNION/value-alignment-protocol.git
cd value-alignment-protocol
pip install -r requirements.txt
cp config/negotiable-values.yaml.example config/negotiable-values.yaml
python -m src.audit.init
```

### Running the Evaluator

```bash
python -m src.evaluator.server --watch-entity OCN-AIR-00001
```

## Integration with AI Rights Registry

VAP consumes entity records from the [AI Rights Registry](https://github.com/GALACTIC-UNION/ai-rights-registry) and writes alignment scores back via the ARR API. Entities with `TIER_3_AUTONOMOUS` rights may submit value amendment proposals directly.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

Apache 2.0 — see [LICENSE](LICENSE).