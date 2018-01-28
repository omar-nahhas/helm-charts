# Keepalived Cloud Provider Helm Chart

This helm chart will install keepalive-vip in your cluster. This chart is only a small addition to the awesome work done in these two github repositories.

- <https://github.com/aledbf/kube-keepalived-vip>

## TL;DR

It expose kuberentes services to the outside world on a predictable ip/port.

In development environments like minikube. It can help you to  expose services like jenkins on a specific ip/port WITHOUT the need of port-forwarding or querying minikube for its ip and the service NodePort.


### Configuration

```yaml
Configuration:
  Services:
   - Vip: 192.168.99.200
     ServiceNamespace: my-cicd-domain
     ServiceName: jenkins
```

This configuration (in the `values.yaml`) will assign the fix ip (192.168.99.200) to your jenkins service deployed in `my-cicd-namespace`. Provided that the port specified on your service is `80`, you should be able to access jenkins on http://192.168.99.200 from your host machine (your laptop running minikube).

### Usage

#### Create the value file (values.yaml)

```yaml
Configuration:
  Services:
   - Vip: 192.168.99.200
     ServiceNamespace: my-cicd-domain
     ServiceName: jenkins
```

#### Install the helm chart

```bash
helm install kube-keepalived-vip -f values.yaml
```
##### Alternatively
This chart is hosted on a GitHub Pages backed helm repository (sourced from this especific repo), so if you could install it from it too.
```
helm repo add foo https://omar-nahhas.github.io/helm-charts
helm repo update
helm install foo/kube-keepalived-vip -f values.yaml
```
