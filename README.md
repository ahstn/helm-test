# Helm Test

Testing out support for building up "bundles" of apps using sub-charts like
lego.

## Structure
```yaml
# Umbrella / Bundle Chart
- marketplace
  - configmap.yaml
  - secrets.yaml
  - values.yaml
  - dependencies
    - auth/
    - billing/
    - payments/

# Explicit Host Entry Values
- hosts/
  - dev-values.yaml

# Individual Service Charts
- auth/
  - service.yaml
  - deployment.yaml
  - values.yaml
- billing/
  - service.yaml
  - deployment.yaml
  - values.yaml
- payments/
  - service.yaml
  - deployment.yaml
  - values.yaml
```

## Usage
```bash
# Fetch deps of marketplace
helm dep up marketplace

# Render bundle as Kubernetes Manifest
helm template marketplace -n $YOUR_RELEASE_VERSION

# Override with dev-hosts.yaml
helm template marketplace -n $YOUR_RELEASE_VERSION -f hosts/dev-values.yaml
```
