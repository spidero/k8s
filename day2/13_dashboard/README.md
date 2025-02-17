```sh
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.4.0/aio/deploy/recommended.yaml
```

create admin-user/rbac

```sh
kubectl create -f admin-user.yaml
kubectl create -f rbac-admin.yaml
```

find admin user:
```sh
kubectl -n kubernetes-dashboard get secret
kubectl -n kubernetes-dashboard describe secret admin-user-token-<id>
```

or
```sh
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret  -o jsonpath='{.items[0].metadata.name}')
```

```sh
kubectl get svc -n  kubernetes-dashboard
kubectl edit svc/kubernetes-dashboard -n  kubernetes-dashboard
edit `type: ClusterIP` to`type: NodePort`
```
or

```sh
kubectl proxy
```
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=default