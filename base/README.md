# Base configuration

```yaml
commonLabels:
  app: vertical-pod-autoscaler
```

Add this label to every resource and use it in any `selector`s.

```yaml
imageTags:
- name: k8s.gcr.io/vpa-admission-controller
  newTag: 0.3.0
- name: k8s.gcr.io/vpa-recommender
  newTag: 0.3.0
- name: k8s.gcr.io/vpa-updater
  newTag: 0.3.0
```

Use these tags for every container image with the given names.

```yaml
namespace: kube-system
```

Install resources into this namespace.

```yaml
resources:
- actor-rbac.yaml
- admission-controller.yaml
- crds.yaml
- recommender.yaml
- updater.yaml
```

Create the resources defined within these files.
