# helm-charts

This repository contains helm charts that ether are modifications of the original helm charts hosted on kuberentes/charts or are charts that are not yet present there.

To start using this charts you need to add the helm chart repository url.

```
helm repo add coolrepo https://omar-nahhas.github.io/helm-charts/
helm repo update
helm install coolrepo/coolchart
```

## acknowledgement 
This helm repository is being created using the following helm plugin.
<https://github.com/technosophos/helm-github>

