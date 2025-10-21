# Helm chart for Gitea Act Runner



Act Runners for Gitea Actions.

![Version: 0.2.2](https://img.shields.io/badge/Version-0.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.2.11](https://img.shields.io/badge/AppVersion-0.2.11-informational?style=flat-square)

## Installing the Chart

To install the chart with the release name `act-runner`

```console
$ helm repo add ay-mirrors https://aaronyang0628.github.io/charts
$ helm install act-runner ay-mirrors /act-runner
```

## Source Code

* <https://github.com/AaronYang0628/act-runner-chart>


## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Affinity and anti-affinity rules for runner pod scheduling. [Affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity). |
| autoscaling.enabled | bool | `false` | Enable horizontal pod autoscaling. |
| autoscaling.maxReplicas | int | `100` | Maximum number of replicas. |
| autoscaling.minReplicas | int | `1` | Minimum number of replicas. |
| autoscaling.targetCPUUtilizationPercentage | int | `80` | Target CPU utilization percentage for scaling. |
| autoscaling.targetMemoryUtilizationPercentage | int | `80` | Target memory utilization percentage for scaling. |
| env | list | See [values.yaml](./values.yaml) for default configuration | Define environment variables for the runner container. |
| envFrom | list | `[]` | Define environment variables from existing ConfigMap or Secret data. |
| extraContainers | list | `[]` | Additional sidecar containers to run alongside the runner container. |
| extraVolumeMounts | list | `[]` | Additional volume mounts for the runner container. |
| extraVolumes | list | `[]` | Additional volumes to attach to the runner pods. |
| global.commonLabels | object | `{}` | Apply labels to all resources. |
| global.fullnameOverride | string | `""` | Override the fully qualified app name. |
| global.nameOverride | string | `""` | Override the name of the app. |
| image.name | string | `"gitea/act_runner"` | Specify the image name to use (relative to `image.repository`). |
| image.pullPolicy | string | `"IfNotPresent"` | Specify the image pull policy. Valid values are `Always`, `Never`, `IfNotPresent`. [imagePullPolicy](https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy). |
| image.pullSecrets | list | `[]` | Specify the image pull secrets if pulling from private registry [imagePullSecrets](https://kubernetes.io/docs/concepts/containers/images/#specifying-imagepullsecrets-on-a-pod). |
| image.repository | string | `"docker.io"` | Specify the image repository to use. |
| image.tag | string | `"0.2.11"` | Overrides the image tag whose default is the chart appVersion. |
| initContainers | list | `[]` | Init containers to run before the main runner container. |
| lifecycle | object | `{}` | Lifecycle hooks for the runner container. [Lifecycle](https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/). |
| livenessProbe | object | `{}` | Liveness probe configuration for the runner container. [LivenessProbe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes). |
| nodeSelector | object | `{}` | Node selector for scheduling runner pods on specific nodes. [nodeSelector](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#nodeselector). |
| persistence.accessModes | string | `"ReadWriteOnce"` | Access modes for the PersistentVolumeClaim. |
| persistence.enabled | bool | `true` | Enable persistent storage for runner data. |
| persistence.mountPath | string | `"/data"` | Path inside the container where the volume will be mounted. |
| persistence.selector | object | `{}` | Label selectors for the PersistentVolumeClaim. |
| persistence.size | string | `"1Gi"` | Size of the PersistentVolumeClaim. |
| persistence.storageClassName | string | `""` | Storage class name for the PersistentVolumeClaim. |
| podAnnotations | object | `{}` | Annotations to add to the runner pods. |
| podLabels | object | `{}` | Labels to add to the runner pods. |
| podPriorityClassName | string | `""` | Priority class name for the runner pods. [priorityClassName](https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/#priorityclass). |
| podSecurityContext | object | `{"fsGroup":1000}` | Pod security context configuration. Only applied when using rootless container. [PodSecurityContext](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/). |
| readinessProbe | object | `{}` | Readiness probe configuration for the runner container. [ReadinessProbe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#configure-probes). |
| replicas | int | `1` | Number of runner replicas. |
| resources | object | `{}` | Resource requests and limits for the runner container. [Resources](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/). |
| runner.config.data | string | See [values.yaml](./values.yaml) for default configuration | Specify runner's custom configuration in YAML format. |
| runner.config.enabled | bool | `false` | Enable custom configuration for the runner deployment. |
| runner.instanceURL | string | `"https://gitea.example.com"` | Gitea instance URL where the runner will register. |
| runner.token.fromSecret.key | string | `""` | Specify the key in the secret that contains the Runner registration token. |
| runner.token.fromSecret.name | string | `""` | Specify the secret name containing the Runner registration token. |
| runner.token.value | string | `""` | Set the Runner registration token value. If existing secret is specified this value is not used. |
| runner.updateStrategy.type | string | `"RollingUpdate"` | Specify the update strategy used to replace old Pods by new ones valid options are `RollingUpdate`, `OnDelete`. [strategy](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/#update-strategies) |
| securityContext | object | `{}` | Security context configuration for the runner container. [SecurityContext](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/). |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account. |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created. |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template. |
| terminationGracePeriodSeconds | int | `10` | Termination grace period in seconds for the runner pods. |
| tolerations | list | `[]` | Tolerations for scheduling runner pods on nodes with taints. [Tolerations](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/). |
| topologySpreadConstraints | list | `[]` | Topology spread constraints for distributing runner pods across zones/nodes. [TopologySpreadConstraints](https://kubernetes.io/docs/concepts/scheduling-eviction/topology-spread-constraints/). |


### Developer CheatSheet
```shell
helm lint ./charts/act-runner
```

```shell
helm package --destination /tmp/ ./charts/act-runner
```

```shell
helm upgrade  --create-namespace -n application --install -f ./charts/act-runner/values.yaml act-runner /tmp/act-runner-0.2.2.tgz
```