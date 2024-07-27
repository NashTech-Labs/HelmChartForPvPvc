# persistentVolume

A Helm chart for creating Persistent Volume (PV) and Persistent Volume Claim (PVC) with Azure Blob CSI Driver for storing Tomcat logs.

## Prerequisites

- Kubernetes 1.17+
- Helm 3+
- Azure Blob Storage Account

## Installation

To install the chart with the release name `persistentVolume`:

```sh
helm install persistentVolume ./persistentVolume
```

## Uninstallation

To uninstall/delete the `persistentVolume` deployment:

```sh
helm uninstall persistentVolume
```

This command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the persistentVolume chart and their default values.

| Parameter                 | Description                                               | Default                    |
|---------------------------|-----------------------------------------------------------|----------------------------|
| `storageClassName`        | Storage class name                                        | `azureblob-csi`            |
| `pv.name`                 | Name of the Persistent Volume                             | `tomcat-logs-pv`           |
| `pv.size`                 | Size of the Persistent Volume                             | `10Gi`                     |
| `pv.accessModes`          | Access modes for the Persistent Volume                    | `[ReadWriteOnce]`          |
| `pvc.name`                | Name of the Persistent Volume Claim                       | `tomcat-logs-pvc`          |
| `pvc.size`                | Size of the Persistent Volume Claim                       | `10Gi`                     |
| `pvc.accessModes`         | Access modes for the Persistent Volume Claim              | `[ReadWriteOnce]`          |

You can specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```sh
helm install persistentVolume ./persistentVolume --set pv.size=20Gi,pvc.size=20Gi
```

Alternatively, you can edit the `values.yaml` file to set the parameters.

## Example

Here is an example `values.yaml` for reference:

```yaml
storageClassName: "azureblob-csi"
pv:
  name: "tomcat-logs-pv"
  size: "10Gi"
  accessModes:
    - ReadWriteOnce

pvc:
  name: "tomcat-logs-pvc"
  size: "10Gi"
  accessModes:
    - ReadWriteOnce
```

## Notes

- Ensure that the `storageAccount` in the `pv.yaml` template is replaced with your actual Azure Storage Account name.
- Make sure the Azure Blob CSI Driver is installed and configured in your Kubernetes cluster.


