# TM overlay

```yaml
bases:
- github.com/ticketmaster/vertical-pod-autoscaler-config//base
```

Use the manifests in the `/base` directory of this repository as the base for this overlay.

```yaml
commonLabels:
  app: vertical-pod-autoscaler
  inventoryCode: vertical-pod-autoscaler
  productCode: prd354
```

Add/substitute these labels on every resource created by the base & overlay and use them in any `selector`s.

```yaml
namespace: prd354
```

Install resources into this namespace.

```yaml
patches:
- admission-controller-deployment.yaml
- recommender-deployment.yaml
- updater-deployment.yaml
```

Apply these patches to the resources they describe.

```yaml
resources:
- tls-certs-secret.yaml
```

Create the resource(s) defined within this file in addition to those defined in the base.

**NOTE**: `tls-certs-secret.yaml` contains self-signed TLS assets generated by `bin/gencerts.sh` with the  `NAMESPACE` variable set to `prd354`. We highly recommend you not use this secret and instead generate your own.