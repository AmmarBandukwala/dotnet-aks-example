[Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

az login

az account set --subscription {GUID}

az aks get-credentials -g aks -n aks-demo

kubectl get nodes

kubectl apply -f .\deployment.yml

kubectl get deployment

kubectl get pods

az aks browse -g aks -n aks-demo

(Must be executed before you can access the kubernetes dashboard)

kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard

kubectl get all

kubectl delete deployment.apps/dotnetapi-deployment

kubectl delete service/dotnetapi-service
