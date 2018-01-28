# Keepalived Cloud Provider Helm Chart

This helm chart will install keepalive-vip and keepalive-vip cloud provider in your cluster. This chart is only a small addition to the awesome work done in these two github repositories.

- <https://github.com/aledbf/kube-keepalived-vip>
- <https://github.com/munnerz/keepalived-cloud-provider>

## TL;DR

I Used for development purpose only, it helps to expose services on a predictable ip and port to your host machine. For example you can expose jenkins(deployed in minikube) always ip a.b.c.d. and on the jenkins configured port (i.e. 80) WITHOUT the need of port-forwarding or querying minikube for its ip and the service NodePort.  


### Configuration

```
Configuration:
  Services:
   - Vip: 192.168.99.200
     ServiceNamespace: my-cicd-domain
     ServiceName: jenkins
LoadBalancers:
  CIDR: 192.168.77.128/25     
```

This configuration (in the `values.yaml`) will assign the fix ip (192.168.99.200) to your jenkins service deployed in `my-cicd-namespace`. Provided that the port specified on your service is `80`, you should be able to access jenkins on http://192.168.99.200 from your host machine (your laptop running minikube).

In addition, the second section of the configuration will allow your LoadBalancer service to adquire an ip from that subnet. If you have made sure that the provided CIDR is the same where minikube is running, then you will be able to access all the LoadBalancer services from your host machine (as in the previous example). If you do not need this feature you can disable it by removing the load balancer section.

### Usage

#### Create the value file (values.yaml)
```
Configuration:
  Services:
   - Vip: 192.168.99.200
     ServiceNamespace: my-cicd-domain
     ServiceName: jenkins
LoadBalancers:
  CIDR: 192.168.77.128/25     
```

#### Install the helm chart
```
helm install kube-keepalived-vip -f values.yaml
```