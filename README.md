# helm-velero

Installs the [Velero](https://velero.io/) Helm chart using Crossplane and the Helm provider. Velero provides backup and restore capabilities for Kubernetes clusters.

## Usage

```yaml
apiVersion: helm.hops.ops.com.ai/v1alpha1
kind: Velero
metadata:
  name: velero
  namespace: my-namespace
spec:
  clusterName: my-cluster
```

## Configuration

| Field | Description | Default |
|-------|-------------|---------|
| `spec.clusterName` | Name of the target cluster | Required |
| `spec.namespace` | Namespace for the Helm release | `velero` |
| `spec.name` | Helm release name | XR metadata.name |
| `spec.labels` | Custom labels merged with defaults | `{}` |
| `spec.values` | Helm values merged with defaults | `{}` |
| `spec.overrideAllValues` | Helm values replacing all defaults | `{}` |
| `spec.providerConfigRef.name` | ProviderConfig name | `clusterName` |
| `spec.providerConfigRef.kind` | ProviderConfig kind | `ProviderConfig` |

## Examples

See the `examples/` directory for usage examples:

- `minimal.yaml` - Basic installation
- `standard.yaml` - Installation with AWS S3 backup storage configuration
