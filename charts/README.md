# Helm Charts

Here are the Helm chart resources of the Eclipse IoT Packages™ project.

## Local Setup

In order to install a Helm chart locally (e.g. in order to enhance a chart), follow the instructions in this section.

### Requirements

* [Kubernetes IN Docker](https://github.com/kubernetes-sigs/kind)
* [kubectl](https://kubernetes.io/docs/tasks/kubectl/install/)
* [Helm v3](https://docs.helm.sh/using_helm/#installing-helm)

### Prepartion

#### Start KIND Cluster

Prepare a kind configuration file named `kind-config.yaml`, with following content:

```yaml
kind: Cluster
apiVersion: kind.sigs.k8s.io/v1alpha3
nodes:
# the control plane node config
- role: control-plane
# Worker reachable from local machine
- role: worker
  extraPortMappings:
  # HTTP
  - containerPort: 32080
    hostPort: 80
```

Start kind cluster

```bash
kind create cluster --image "kindest/node:v1.14.10" --config kind-config.yaml
```

### Install a Chart

**Note:** Following commands requires Helm v3

With the following command, the Ditto chart is installed as an example

```bash
helm upgrade eclipse-ditto ditto/ --install
```

Follow the instructions from `NOTES.txt` (printed when install is finished).

### Delete a Helm Release

```bash
helm delete eclipse-ditto
```

### Destroy KIND Cluster

```bash
kind delete cluster
```

### Troubleshooting

If you experience high resource consumption (either CPU or RAM or both), you can limit the resource usage by specifing resource limits.
This can be done individually for each single component.
Here is an example how to limit CPU to 0.25 Cores and RAM to 512MiB for the `connectivity` service:

```bash
helm upgrade eclipse-ditto . --install --set connectivity.resources.limits.cpu=0.25 --set connectivity.resources.limits.memory=512Mi
```
