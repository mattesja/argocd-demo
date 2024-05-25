# Demonstration to show using waves in app-of-app pattern

## Prerequisites

### Install ArgoCD via Helm

~~~
helm repo add argo https://argoproj.github.io/argo-helm
helm install -n argocd argo argo/argo-cd
~~~

### Create ArgoCD Parent Application
~~~
kubectl apply -f bootstrap-application.yaml
~~~

## Testing

- Do initial sync via ArgoCD UI
- Update image tag in values.yaml
- Sync again via ArgoCD UI
- Hooks will update the child applications in the correct order



