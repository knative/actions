# Downstream Test

This action allows you to target a downstream repository to upgrade with the
version of the upstream repository and then run the unit tests.

This action assumes go modules and repo setup is similar to Knative and that
environmental setup has already been performed.

## Usage

```yaml
- uses: knative/actions/go/downstream-test@main
  with:
    # Path to upstream module. For example, ./knative.dev/pkg
    # Required
    upstream-path: ""

    # Path to downstream module. For example, ./knative.dev/sample-controller
    # Required.
    downstream-path: ""
```

## Scenarios

### Test knative.dev/pkg changes are accepted by knative.dev/sample-controller

```yaml
steps:
  - name: Set up Go 1.19.x
    uses: actions/setup-go@v3
    with:
      go-version: 1.19.x
  - name: Checkout Upstream
    uses: actions/checkout@v3
    with:
      repository: knative/pkg
      path: pkg
  - name: Checkout Downstream
    uses: actions/checkout@v3
    with:
      repository: knative-sandbox/sample-controller
      path: controller
  - uses: knative/actions/go/downstream-test@main
    with:
      upstream-path: pkg
      downstream-path: sample-controller
```
