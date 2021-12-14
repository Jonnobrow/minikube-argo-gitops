# Minikube Argo Gitops

Working through [this guide](https://www.arthurkoziel.com/setting-up-argocd-with-helm/) to learn how to use [argo](https://argoproj.github.io/)

## Prerequisites
- [minikube](https://minikube.sigs.k8s.io/docs/)
- [helm](https://helm.sh/)
- optionally: [kubectl](https://kubernetes.io/docs/tasks/tools/)

## Running
1. Start a minikube cluster
    ```bash
    minikube start
    ```
2. Bootstrap the cluster
    ```bash
    helm install argo-cd charts/argo-cd
    ```
