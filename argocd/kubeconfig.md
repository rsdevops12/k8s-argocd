kubeconfig, обычно хранит свою конфигурацию в ~/.kube/config, она нужна чтобы kubectl понимал какой кластер вообще работает, и к какому Kubernetes API server-у обращаться.

В очень редких случаях может возникнуть инцидент, когда ты разворачиваешь кластер куба, дальше удаляешь кластер, а потом снова поднимаешь, может возникнуть такая проблема что kubeconfig не обновился, и id/hash кластера старый

#### Проверить можно:
```bash
kubectl config get-clusters
kubectl config get-contexts
kubectl config get-users
```

##### Удалить старый кластер:
```bash
kubectl config delete-cluster old-cluster
```

##### Удалить старого пользователя:
```bash
kubectl config delete-user old-user
```

##### Удалить старый контекст:
```bash
kubectl config delete-context old-context
```

на проде руками такое не меняют, потому что сам куб автоматически настраивает kubeconfig, но если что на заметку )))