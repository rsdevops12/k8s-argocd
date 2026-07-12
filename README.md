## Установить Argo CD

```bash
kubectl create namespace argocd
```

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
правда используется stable версия, рекомендуется перейти по ссылке https://github.com/argoproj/argo-cd/releases/ и выбрать там последную версию


## Запустить Argo CD API Server, для локального подключения по localhost если находишься в одной подсети

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```


## Запустить Argo CD API Server, для подключения по ip_addr_machine:port

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443 --address 0.0.0.0 &
```

## Посмотреть пароль системы для admin пользователя

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

полезные ссылки на argocd:
https://github.com/argoproj/argo-cd/releases/
https://argo-cd.readthedocs.io/en/stable/getting_started/
