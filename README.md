# ArgoCD umberalla helm chart

Argo CD will not use helm install to install charts. It will render the chart with helm template and then apply the output with kubectl so can’t run `helm list` to list installed releases.

## Usage

To deploy our root application we need to apply the manifests deploying `root` and `argo` apps:
    $ helm repo add argo-cd https://argoproj.github.io/argo-helm
    $ helm install argo-cd charts/argo-cd
    $ helm template apps/ | kubectl apply -f -

Once Argo is syncronised and self-managing, remove the application from helm management:
    $ kubectl delete secret -l owner=helm,name=argo-cd