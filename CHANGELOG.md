# Changelog

## Unreleased
- Added standalone CLI (`cmd/yamlvalidator`) that validates YAML using a schema described in YAML/JSON (serialized FieldSchema), with flags for strict keys, YAML 1.1 booleans, type strictness, and stop-on-first.
- Added schema loader tests for YAML/JSON inputs and validation of validator names.
- Refactored `examples/easyp` to share its schema via `examples/easyp/schema` instead of defining validators inline.

## v0.1.0
- Initial release of `go-yamlvalidator`:
  - YAML 1.2 validation core with optional YAML 1.1 boolean support.
  - Schema-driven validation: types, required/nullable/default/deprecated, maps/sequences, unknown key policies, inter-field rules (AnyOf/ExactlyOneOf/MutuallyExclusive/Conditions), multi-document and alias handling, position-aware error formatting.
  - Built-in validators split into packages:
    - `pkg/valuevalidator`: enum, regex, range, non-empty, length, URL, one-of-type, custom easyp validators.
    - `pkg/keyvalidator`: regex, forbidden, length (rune-count aware).
  - Public helpers: pointer helpers, exported caret renderer, type inference helper for external validators.
  - Examples: Kubernetes-like validation (`examples/basic`) and `easyp` config validator (`examples/easyp`), plus README guides for key/value validators and settings.
  - Tests: coverage for types, nullability, unknown keys, sequences, inter-field logic, YAML 1.1 booleans, aliases, formatting, merge keys, numeric parsing in RangeValidator, Unicode key lengths, and position sorting.
