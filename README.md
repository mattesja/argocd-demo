# ArgoCD Demo: How to use sync waves in app-of-app pattern

There's a blogpost, which describes how use of waves in an app-of-app pattern: https://codefresh.io/blog/argo-cd-application-dependencies/ <br>
Unfortunately, this does not work for every of our use-cases.

So, it's not possible to deploy new versions of the child applications in the correct order:
https://github.com/argoproj/argo-cd/issues/8778#issuecomment-1069168965

Therefore, we introduces sync hooks, which trigger the sync of the child applications.  

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



