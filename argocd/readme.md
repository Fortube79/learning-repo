# 1. Installing Argo CD into Kubernetes cluster

## 1.1. Using kubectl command-line tool
$kubectl create namespace argocd
$kubectl -n argocd apply -f . 
or
$kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml 

## 1.2. Service Type Load Balancer
To change the argocd-server service type to LoadBalancer, la argo-install.yaml ya esta en type=loadbalancer
$kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'


## 1.3. Obtener Password Inicial
$kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode