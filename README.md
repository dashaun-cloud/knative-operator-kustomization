# Knative Operator Kustomization

For use with [FluxCD](https://fluxcd.io) to deploy the [Knative Operator](https://knative.dev)

## Add the GitRepository

```bash
flux create source git knative-operator \
  --url=https://github.com/dashaun-cloud/knative-operator-kustomization \
  --branch=main \
  --interval=30s \
  --export > ./clusters/cluster00/knative-operator-source.yaml
```

## Add the Kustomization

```bash
flux create kustomization knative-operator \
  --target-namespace=default \
  --source=knative-operator \
  --path="./kustomize" \
  --prune=true \
  --interval=5m \
  --export > ./clusters/cluster00/knative-operator-kustomization.yaml
```