# Hawkbit Update Server

## Introduction

[Eclipse hawkBit™](https://www.eclipse.org/hawkbit/) is a domain independent back-end framework for rolling out software updates to constrained edge devices as well as more powerful controllers and gateways connected to IP based networking infrastructure.

This chart uses hawkbit/hawkbit-update-server container to run Hawkbit update server inside Kubernetes.

## Prerequisites

- Has been tested on Kubernetes 1.11+

## Installing the Chart

To install the chart with the release name `hawkbit-update-server`, run the following command:

```bash
helm install eclipse-iot/hawkbit-update-server --name hawkbit-update-server
```

## Uninstalling the Chart

To uninstall/delete the `hawkbit-update-server` deployment:

```bash
helm delete hawkbit-update-server
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

> **Tip**: To completely remove the release, run `helm delete --purge hawkbit-update-server`

## Configuration

Please view the `values.yaml` for the list of possible configuration values with its documentation.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```bash
helm install hawkbit-update-server eclipse-iot/hawkbit-update-server --set podDisruptionBudget.enabled=true
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart.
