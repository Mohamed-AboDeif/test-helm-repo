# iVoiceUp Helm Chart Repository

A Helm repository for iVoiceUp Kubernetes charts.

## Adding the Repository

```bash
helm repo add ivoiceup https://ivoiceup.github.io/ivoiceup-app-chart/
helm repo update
```


## Available Charts

| Chart | Version | Description |
|-------|---------|-------------|
| `service` | 1.18.7 | Generic Helm chart for deploying iVoiceUp microservices on Kubernetes |
| `sockudo` | 0.1.0 | WebSocket server implementing the Pusher protocol |

## Installing Charts

### service

```bash
helm install my-service ivoiceup/service \
  --set image.repository=<your-ecr-repo> \
  --set image.tag=<your-tag>
```

### sockudo

```bash
helm install my-sockudo ivoiceup/sockudo
```

## Configuration

See the `values.yaml` in each chart directory for all available configuration options:

- [`charts/service/values.yaml`](charts/service/values.yaml)
- [`charts/sockudo/values.yaml`](charts/sockudo/values.yaml)

## Upgrading a Chart

```bash
helm repo update
helm upgrade my-service ivoiceup/service --reuse-values
```

## CI/CD

This repository uses [helm/chart-releaser-action](https://github.com/helm/chart-releaser-action) to automatically:

1. Package updated charts on push to `main` or `helm-stg`
2. Create a GitHub Release with the packaged `.tgz` as an asset
3. Update the `index.yaml` on the `gh-pages` branch

### GitHub Pages Setup

Enable GitHub Pages in the repository settings:
- **Source**: Deploy from branch
- **Branch**: `gh-pages` / `/ (root)`

The Helm repository will be available at:
```
https://ivoiceup.github.io/ivoiceup-app-chart/
```
