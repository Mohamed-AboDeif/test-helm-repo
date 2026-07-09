# service

![Version: 1.18.5](https://img.shields.io/badge/Version-1.18.5-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

A Helm chart for Kubernetes

**Homepage:** <https://github.com/registfyrepos/helm-chart>

## Source Code

* <https://github.com/registfyrepos/helm-chart>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Pod affinity rule. Default affinity rule is set to make sure pods are not deployed on the same node |
| annotations | object | `{}` | Deployment annotations |
| containerPort | int | `80` | Docker container port |
| env | string | `"dev"` | Environment |
| envFrom | list | `[]` | Environment list from kubernetes secrets |
| environment | list | `[]` | Environment variable list |
| externalSecret.backendType | string | `"vault"` | backend type. vault or systemManager. Default: vault |
| externalSecret.data | list | `[]` | List of map of objects to fetch from the secret backend. |
| externalSecret.dataFrom | list | `[]` | dataFrom is used to retrieve all values from a specific path. |
| externalSecret.enabled | bool | `false` | If true, externalSecret will be created |
| externalSecret.vaultMountPoint | string | `"kubernetes-finx-qa-eks-cluster"` | Required when backendType is vault. Change this EKS cluster name. Remove this when backendType is systemManager |
| externalSecret.vaultRole | string | `"external-secrets"` | Required when backendType is vault. Remove this when backendType is systemManager |
| fullnameOverride | string | `""` |  |
| horizontalPodAutoscaler.behavior.scaleDown.policies[0].periodSeconds | int | `15` |  |
| horizontalPodAutoscaler.behavior.scaleDown.policies[0].type | string | `"Percent"` |  |
| horizontalPodAutoscaler.behavior.scaleDown.policies[0].value | int | `100` |  |
| horizontalPodAutoscaler.behavior.scaleDown.stabilizationWindowSeconds | int | `300` |  |
| horizontalPodAutoscaler.behavior.scaleUp.policies[0].periodSeconds | int | `15` |  |
| horizontalPodAutoscaler.behavior.scaleUp.policies[0].type | string | `"Percent"` |  |
| horizontalPodAutoscaler.behavior.scaleUp.policies[0].value | int | `100` |  |
| horizontalPodAutoscaler.behavior.scaleUp.policies[1].periodSeconds | int | `15` |  |
| horizontalPodAutoscaler.behavior.scaleUp.policies[1].type | string | `"Pods"` |  |
| horizontalPodAutoscaler.behavior.scaleUp.policies[1].value | int | `4` |  |
| horizontalPodAutoscaler.behavior.scaleUp.selectPolicy | string | `"Max"` |  |
| horizontalPodAutoscaler.behavior.scaleUp.stabilizationWindowSeconds | int | `0` |  |
| horizontalPodAutoscaler.enabled | bool | `false` | Whether to enable hpa. Set to true for Prod |
| horizontalPodAutoscaler.maxReplicas | int | `6` | maximum number of replicas. Set this value as 6x of the minimum pods |
| horizontalPodAutoscaler.metrics[0].resource.name | string | `"cpu"` |  |
| horizontalPodAutoscaler.metrics[0].resource.target.averageUtilization | int | `75` | CPU target average utilization of the pods to trigger scalie |
| horizontalPodAutoscaler.metrics[0].resource.target.type | string | `"Utilization"` |  |
| horizontalPodAutoscaler.metrics[0].type | string | `"Resource"` |  |
| horizontalPodAutoscaler.minReplicas | int | `1` | when true, this value should be equal to number of replicas in deployment. Must be >1 for production |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"1234567890.dkr.ecr.eu-west-2/demo"` | ECR Repository. This value must be changed to match service ECR repo |
| image.tag | string | `"v0.1"` | ECR image tag |
| imagePullSecrets | list | `[]` |  |
| ingress.enabled | bool | `true` |  |
| ingress.rules[0] | string | `"Host(`service.thefinx.io`)"` |  |
| ingress.sticky | bool | `false` |  |
| lifecycle.preStop | object | `{"exec":{"command":["/bin/sh","-c","sleep 2"]}}` | Pre stop command to run just before handling a termination request from API. This helps in graceful termination of the pods |
| livenessProbe.failureThreshold | int | `3` |  |
| livenessProbe.periodSeconds | int | `15` |  |
| livenessProbe.successThreshold | int | `1` |  |
| livenessProbe.tcpSocket.port | int | `80` |  |
| livenessProbe.timeoutSeconds | int | `2` |  |
| nameOverride | string | `"{{ .Release.Name }}"` |  |
| nodeSelector | object | `{}` | Provide node groups selector |
| podDisruptionBudget.enabled | bool | `false` |  |
| podDisruptionBudget.minAvailable | int | `1` |  |
| podSecurityContext | object | `{}` |  |
| readinessProbe.failureThreshold | int | `3` |  |
| readinessProbe.httpGet.path | string | `"/"` | Readinessprobe healthcheck path |
| readinessProbe.httpGet.port | int | `80` | Readinessprobe port. This should be equal to docker container port in most cases |
| readinessProbe.httpGet.scheme | string | `"HTTP"` |  |
| readinessProbe.periodSeconds | int | `10` |  |
| readinessProbe.successThreshold | int | `1` |  |
| readinessProbe.timeoutSeconds | int | `2` |  |
| replicas | int | `1` | Number of replicas to deploy. When HPA is enabled, this value is being ignored |
| resources.limits.memory | string | `"1Gi"` | Resource memory limit |
| resources.requests.cpu | string | `"250m"` | Resource request cpu |
| resources.requests.memory | string | `"512Mi"` | Resource request memory |
| revisionHistoryLimit | int | `10` |  |
| rollingUpdate.maxSurge | string | `"25%"` |  |
| rollingUpdate.maxUnavailable | string | `"50%"` |  |
| securityContext | object | `{}` |  |
| service.backendProtocol | string | `"http"` | Kong backendProtocol supported by Kong can be either `http` , `https` , `grpc` |
| service.port | int | `80` | Kubernetes service port |
| service.type | string | `"ClusterIP"` | Service type, can be either `ClusterIP`, `NodePort`, `LoadBalancer` or `ExternalName` |
| serviceAccount.annotations | object | `{}` | Provide IAM Role ARN, if create is true. |
| serviceAccount.create | bool | `false` | If true, creates service account |
| serviceAccount.name | string | `""` | If not set and create is true, a name is generated using the fullname template |
| startupProbe.failureThreshold | int | `30` |  |
| startupProbe.initialDelaySeconds | int | `30` |  |
| startupProbe.periodSeconds | int | `10` |  |
| startupProbe.tcpSocket.port | int | `80` | Startupprobe healthcheck port. This should be equal to docker container port in most cases |
| startupProbe.timeoutSeconds | int | `2` |  |
| tolerations | list | `[]` | If node group is tainted, provide pod tolerations to run on specific node groups |
| verticalPodAutoscaler | object | `{"enabled":false}` | If true, vertical-pod-autoscaler is created in `Off` or `Recommendation` updateMode |
| volumeMounts | list | `[]` | List of volumes to attach |
| volumes | list | `[]` | List of volumes to create |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.10.0](https://github.com/norwoodj/helm-docs/releases/v1.10.0)
