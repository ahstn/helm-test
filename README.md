# Helm Test

Testing out support for building up "bundles" of apps using sub-charts like
lego.

## Usage
```bash
# Fetch deps of marketplace
helm dep up marketplace

# Render bundle as Kubernetes Manifest
helm template marketplace -n $YOUR_RELEASE_VERSION
```
