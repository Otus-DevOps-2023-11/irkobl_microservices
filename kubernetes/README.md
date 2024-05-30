
# 30.Ingress-контроллеры и сервисы в Kubernetes

Kubernetes + Proxmox
Pull address: 192.168.222.{51,52,53,54}

```bash
kubectl get nodes
```
![Nodes](https://github.com/irkobl/picture/blob/main/kubernetes/nodes.png)

```bash
kubectl get pods -n dev
```
![Nodes](https://github.com/irkobl/picture/blob/main/kubernetes/pods.png)

# ClusterIP
```bash
kubectl get services -n dev
```
![Nodes](https://github.com/irkobl/picture/blob/main/kubernetes/ClusterIP.png)

# Kube-dns

```bash
# Install autoscale - https://raw.githubusercontent.com/kubernetes/website/main/content/en/examples/admin/dns/dns-horizontal-autoscaler.yaml
kubectl apply -f kubernetes/dns-horizontal-autoscaler.yml
```

```bash
kubectl get configmap --namespace=kube-system
```
![CoreDNS](https://github.com/irkobl/picture/blob/main/kubernetes/CoreDNS.png)


```bash
# Disable horizontal autoscale
kubectl scale deployment --replicas 0 -n kube-system kube-dns-autoscaler
kubectl scale deployment --replicas 0 -n kube-system kube-dns
kubectl get rs --namespace=kube-system
```
![Ping comment](https://github.com/irkobl/picture/blob/main/kubernetes/dnsauto.png)


```bash
# Test ping comment
kubectl exec -ti -n dev post-deployment-65967f9c99-nqgdm ping comment
```
![Ping comment](https://github.com/irkobl/picture/blob/main/kubernetes/ping.png)

# NodePort

![Ping comment](https://github.com/irkobl/picture/blob/main/kubernetes/NodePorts.png)

# LoadBalancer

```bash
kubectl apply -f kubernetes/reddit/ui-service.yml -n dev
kubectl get service -n dev --selector component=ui
```
![Ping comment](https://github.com/irkobl/picture/blob/main/kubernetes/lb.png)

# Ingress 

```bash
# Install Metallb (network load-balancer implementation)
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.5/config/manifests/metallb-native.yaml
kubectl apply -f kubernetes/config-mb.yml
kubectl apply -f kubernetes/reddit/ui-service.yml
kubectl api-resources | grep metallb
```

```bash
# Install ingress (NGINX Ingress Controller)
helm pull oci://ghcr.io/nginxinc/charts/nginx-ingress --untar --version 1.2.1
cd nginx-ingress 
kubectl apply -f crds/
helm install nginx-ingress oci://ghcr.io/nginxinc/charts/nginx-ingress --version 1.2.1
kubectl delete -A ValidatingWebhookConfiguration ingress-nginx-xxxxx-admission
kubectl get pods && kubectl get svc
```
![Pods, svc ingress](https://github.com/irkobl/picture/blob/main/kubernetes/ing.png)

```bash
kubectl apply -f kubernetes/reddit/ui-ingress.yml
kubectl get pods -n dev && kubectl get ingress -n dev
```
![IP ingress](https://github.com/irkobl/picture/blob/main/kubernetes/ing2.png)

```bash
sudo echo 192.168.222.52 app.ui >> /etc/hosts
```
![IP ingress](https://github.com/irkobl/picture/blob/main/kubernetes/ui6.png)

# Secret

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=192.168.222.52"
kubectl create secret tls ui-ingress --key tls.key --cert tls.crt -n dev
kubectl describe secret ui-ingress -n dev
```
![tls ingress](https://github.com/irkobl/picture/blob/main/kubernetes/tls.png)

```bash
kubectl describe ingress -n dev
```
![Describe ingress](https://github.com/irkobl/picture/blob/main/kubernetes/ing3.png)
![HTTPS ui service](https://github.com/irkobl/picture/blob/main/kubernetes/ui7.png)


# 29.Введение в Kubernetes #2

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