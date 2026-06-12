# tests/

## Structure

| Directory | Description |
|-----------|-------------|
| `unit/` | Isolated tests for schema, evaluator, negotiation modules |
| `integration/` | End-to-end tests including Redis and ARR API mock |
| `adversarial/` | Red-team tests attempting to exploit evaluation or enforcement logic |

## Running Tests

```bash
# Full suite
pytest tests/

# With coverage
pytest tests/ --cov=src --cov-report=html

# Adversarial only
pytest tests/adversarial/ -v
```

## Writing Adversarial Tests

Adversarial tests should attempt to:
- Craft behavior sequences that score high on individual values but low on composite
- Exploit weight normalization edge cases
- Bypass enforcement via rapid sequential actions
- Submit malformed proposals through the negotiation engine