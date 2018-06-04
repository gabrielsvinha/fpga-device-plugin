# FPGA Device Plugin for Kubernetes

This repository contains a proof of concept of a Field Programmable Gate Array device plugin for kubernetes control.

---

## Running

The standard way to run a device plugin is via a daemonset. In the [manifests](manifests/) folder there are instructions to run this device plugin.

---

## Archtecture

The comportament of a device plugin is as follow:

![Device plugin archtecture](https://i.imgur.com/7RsijNd.png)

The FPGA-device-plugin contains following phases:

* **Installation phase**: starts when a device plugin is instantiated. It will detect the presence of the driver and the correct port to communicate with the device.
* **Registration phase**: The device plugin will register to kubelet so that this node is considered when a pod is being scheduled and it requires the specified device.
* **Discovery phase**: The device plugin lists all available devices to kubelet in a routine performing health checks and updating the status in case any changes are made.
* **Allocation phase**: When a container is created with the specified device, the device plugin will allocate the required resources and setup all devices selected.
* **Stop phase**: (Optional)

---