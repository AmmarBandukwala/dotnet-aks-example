# Quick Links

[Kubernetes Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) </br>
[Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) </br>
[Kubectl CLI](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

# Command Line Sequences

1. az login

2. az account set --subscription {GUID}

3. az aks get-credentials -g aks -n aks-demo

4. kubectl get nodes

5. kubectl apply -f .\deployment.yml

6. kubectl get deployment

7. kubectl get pods

8. az aks browse -g aks -n aks-demo

## Execute the following sequence if Kubernetes Dashboard not loading correctly.

kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard

kubectl get all

kubectl delete deployment.apps/dotnetapi-deployment

kubectl delete service/dotnetapi-service
