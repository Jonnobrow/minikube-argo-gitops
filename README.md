# Minikube Argo Gitops

Working through [this guide](https://www.arthurkoziel.com/setting-up-argocd-with-helm/) to learn how to use [argo](https://argoproj.github.io/).

The [Declarative Setup](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#app-of-apps) guide is also usefu guide is also useful.

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
    kubectl create ns argocd
    # Install Argo CD
    helm install argo-cd charts/argo-cd -n argocd
    # Install the root app
    helm template apps/ | kubectl apply -f -
    ```
3. Port-forward
    ```bash
    kubectl port-forward -n argocd service/argo-cd-argocd-server 8080:443
    ```
4. Get initial admin password
    ```bash
    kubectl -n argocd get secrets argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
    ```
