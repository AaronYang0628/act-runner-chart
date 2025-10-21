```shell
helm lint .
```

```shell
helm package --dependency-update --destination /tmp/ .
# helm package --destination /tmp/ .
```

```shell
helm repo index .
```

```shell
helm upgrade --create-namespace -n gitea --install -f ./values.yaml act-runner /tmp/act-runner-0.2.2.tgz
```
