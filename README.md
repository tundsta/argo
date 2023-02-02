# ArgoCD umberalla helm chart

Argo CD will not use helm install to install charts. It will render the chart with helm template and then apply the output with kubectl so can’t run `helm list` to list installed releases.

## Usage

To deploy our root application we need to apply the manifest:

    helm template apps/ | kubectl apply -f -