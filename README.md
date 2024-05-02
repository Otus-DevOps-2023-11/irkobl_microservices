
# 28.Введение в Kubernetes #2

## Work pods comment, mongo, ui, post

```bash
kubectl port-forward ui-64cfdb6bf7-pgwgt 8080:9292
```
![UI after](https://github.com/irkobl/picture/blob/main/kubernetes/ui1.png)

### Run all Service

```bash
kubectl port-forward ui-64cfdb6bf7-pgwgt 9292:9292
```
![UI before](https://github.com/irkobl/picture/blob/main/kubernetes/ui2.png)

### Run with nodePort

```bash
minikube service ui
```
![UI nodePort](https://github.com/irkobl/picture/blob/main/kubernetes/ui3.png)

### Run with namespace dev

```bash
minikube service ui -n dev
```
![UI namespace](https://github.com/irkobl/picture/blob/main/kubernetes/ui4.png)

### Deploy in k8s

Add new cluster in ~/.kube/conf

```bash
kubectl cluster-info
kubectl --context kubernetes-admin@kubernetes get nodes
kubectl config use-context kubernetes-admin@kubernetes
kubectl get nodes
kubectl apply -f dev-namespace.yml
kubectl apply -f ./ -n dev
```

![UI another cluster](https://github.com/irkobl/picture/blob/main/kubernetes/ui5.png)






