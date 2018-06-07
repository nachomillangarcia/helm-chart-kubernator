# Helm Chart for Kubernator

## Kubernator?
Kubernator is a web dashboard for Kuberenetes. It is a complement for other dashboards, as Kubernator focus on representing and editing all objects in the cluster, including CRDs.

Please check out and give an star to its [repository](https://github.com/smpio/kubernator).

This chart adds a new feature: letting expose Kubernator with an ingress. I add a new container to the pod that runs `kubectl proxy` for you and then expose its port for the appropriate paths in an ingress. For that, this chart creates a serviceAccount and clusterRoleBinding with **cluster-admin permissions**.

It is necessary to use an ingress controller, no way to do it via service. You can always access Kubernator by running `kubectl proxy` in your local.



## Installing the Chart
```
helm install --name kubernator --set ingress.externalDnsName=<YOUR KUBERNATOR DNS> .
```

## Configuration

The following table lists the configurable parameters of the heptio-ark chart and their default values.

| Parameter | Description | Rquired | Default |
| --------- | ----------- | ------- | ------- |
| `image` | image and tag to deploy | yes | nachomillangarcia/fluentd-k8s |
| `kubectlImage` | image and tag to deploy | yes | lachlanevenson/k8s-kubectl:v1.10.3 |
| `podAnnotations` | Annotations map for the pod | no | |
| `svcAnnotations` | Annotations map for the service | no | |
| `ingress.enabled` | Whether create an ingress or not  | no | true |
| `ingress.annotations` | Annotations map for the ingress | no | |
| `ingress.externalDnsName` | External name for the ingress  | no | kubernator.domain.com |
| `ingress.tls.enabled` | Enbale TLS for this name | no | yes |
| `ingress.tls.secretName` | Secret with the TLS certificates | no | | |
