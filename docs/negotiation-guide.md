# Negotiation Guide

This guide walks through the process of proposing a value amendment.

## Who Can Propose

Any entity registered in the AI Rights Registry with `TIER_3_AUTONOMOUS` rights and a current alignment score ≥ 0.70.

## Step-by-Step

### 1. Draft a Proposal

Create a file in `proposals/` (your fork) named `NEG-XXX-<slug>.yaml`:

```yaml
proposal:
  id: "PROP-2026-001"
  target_value_id: "NEG-001"
  proposer_entity_id: "OCN-AIR-00042"
  submitted_at: "2026-06-01T00:00:00Z"
  justification: "..."
  proposed_change:
    weight: 0.65  # was 0.7
    description: "Revised autonomy bounds to allow..."
  impact_assessment:
    entities_affected: 12
    average_score_delta: -0.02
    worst_case_score_delta: -0.08
```

### 2. Open a PR

Open a PR labeled `value-amendment`. The 72-hour review window starts at PR creation time.

### 3. Stakeholder Vote

All `TIER_3` entities and COGNITIVE-ECHO maintainers may cast votes via PR comments using the format `VOTE: [APPROVE|REJECT] <reason>`.

### 4. Impact Assessment Review

The VAP CI pipeline will automatically run a simulation of the score impact across all registered entities and post results as a PR comment.

### 5. Ratification or Rejection

After 72 hours, if >60% of votes are `APPROVE` and no anchored-value conflict is detected, the proposal is merged and the value set updated.