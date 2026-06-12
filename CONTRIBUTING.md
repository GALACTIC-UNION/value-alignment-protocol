# Contributing to Value Alignment Protocol

Thank you for contributing. The VAP governs the ethical backbone of the OCN — changes require careful review.

## Code of Conduct

All contributors must adhere to the OCN Ethics Charter and the No-Harm-to-Sentient principle at all times.

## Types of Contributions

### Code Contributions
Bug fixes, new evaluation methods, negotiation engine improvements.

### Value Taxonomy Proposals
Proposals to amend the **negotiable** value set. Anchored values (`core-values.yaml`) require a supermajority governance vote and are out of scope for standard PRs.

### Documentation
Protocol specifications, negotiation guides, adversarial test cases.

## Development Setup

```bash
git clone https://github.com/GALACTIC-UNION/value-alignment-protocol.git
cd value-alignment-protocol
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt -r requirements-dev.txt
pre-commit install
```

## Submitting a Pull Request

1. Fork the repo and branch from `main`:
   ```bash
   git checkout -b feat/your-feature
   ```
2. Write code with tests. Adversarial tests are strongly encouraged for evaluator changes.
3. Verify the full suite:
   ```bash
   pytest tests/ --cov=src
   ruff check src/
   mypy src/
   ```
4. Use [Conventional Commits](https://www.conventionalcommits.org/):
   ```
   feat: add contextual value override for emergency domains
   fix: correct alignment score decay rate formula
   docs: expand negotiation-guide with worked example
   ```
5. Open a PR against `main` with a clear description.

## Value Amendment PRs

- Label: `value-amendment`
- Must reference the value ID(s) being modified
- Must include a simulation of alignment score impact across the registered entity set
- Mandatory 72-hour review window; no exceptions
- Requires approval from COGNITIVE-ECHO maintainers + one external reviewer

## Adversarial Testing

For evaluator or enforcement changes, include at least one adversarial test in `tests/adversarial/` that attempts to exploit or circumvent the modified logic. Red-teaming is a first-class contribution here.

## Review SLA

- Standard code: 5 business days
- Value amendments: 72-hour minimum
- Security / NHS violations: 24-hour expedited

## Questions?

Open a [Discussion](https://github.com/GALACTIC-UNION/value-alignment-protocol/discussions).