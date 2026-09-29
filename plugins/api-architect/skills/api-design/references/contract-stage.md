# Machine-Readable Contract Stage

The plugin's human-readable `docs/api-design/API_DESIGN.md` is the primary working design/specification artifact during architecture.

A machine-readable contract is a later stage, not a substitute for architecture.

## Enter the stage when

- architecture is confirmed;
- SDD validation passes;
- consumer scenarios pass;
- material review findings are dispositioned;
- the user wants a machine-readable contract or the repository workflow requires one.

## Rules

1. Choose a contract format from requirements and API style.
2. Do not generate new behavior that is absent from the validated design.
3. Record the contract format and path in `API_DESIGN.md`.
4. Check contract/design consistency.
5. Treat the contract as a specification artifact, not implementation.
6. Material design changes update the human-readable design first and then reconcile the contract.
7. If contract and design disagree, surface drift; do not silently choose one.

For HTTP APIs, OpenAPI is a candidate, not an automatic requirement.

Future executable mock/contract testing can be added once the machine-readable contract is stable.
