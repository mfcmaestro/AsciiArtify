
## Introduction
The aim of this article is to compare the functionality of the most widely used lightweight K8S implementations, including minikube, k3d, and kind. This information will help the company make a decision on which tool is best suited for our needs.

## Tools overview

### Minikube

Minikube is an open-source tool that allows you to set up a single-node Kubernetes cluster on your local machine. It provides an environment where you can deploy, manage, and test Kubernetes applications without the need for a full-scale production cluster. Minikube is particularly useful for developers who want to experiment with Kubernetes features, test configurations, and develop applications before deploying them to a real cluster.

#### Demonstration

![minikube_demo](../blob/gifs/minikube.gif)

### k3d

K3d, developed by Rancher, is a lightweight Kubernetes distribution tailored for IoT and Edge devices. Operating seamlessly on most modern Linux systems, it furnishes a VM-based Kubernetes environment. Here, users have the flexibility to manually configure nodes and virtual machines to orchestrate multiple Kubernetes servers.

A standout feature of K3d is its suitability for testing production environments locally, offering a solution for developers to simulate real-world scenarios with ease. Its efficient design ensures a low memory footprint, achieved by excluding certain features from the Kubernetes binary without compromising functionality.

K3d streamlines the deployment process with its auto-deployment feature, enabling users to effortlessly deploy Kubernetes manifests and helm charts by simply placing them in a designated directory. It opts for SQLite as its default storage backend instead of etcd3, enhancing its performance and resource efficiency.

Designed with performance-constrained environments like IoT in mind, K3d incorporates various features such as Local Storage Provider, Service Load Balancer, Helm Controller, among others, catering to the specific needs of such deployments. With its lightweight nature and focus on resource optimization, K3d stands out as an ideal solution for Kubernetes orchestration in challenging environments.

#### Demonstration

![k3d_demo](../blob/gifs/k3d.gif)

### Kind

kind or kubernetes in docker is a suite of tooling for local Kubernetes “clusters” where each “node” is a Docker container. kind is targeted at testing Kubernetes.

kind is divided into go packages implementing most of the functionality, a command line for users, and a “node” base image. The intent is that the kind suite of packages should eventually be importable and reusable by other tools (e.g. kubetest) while the CLI provides a quick way to use and debug these packages.

In short kind targets local clusters for testing purposes. While not all testing can be performed without “real” clusters in “the cloud” with provider enabled CCMs, enough can that we want something that:

#### Demonstration

![kind_demo](../blob/gifs/kind.gif)

## Comparison Table

|                                | Minikube                                                                                        | kind                                | k3d                                 |
|--------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------|-------------------------------------|
| **OS**                         | Linux, MacOS, Windows                                                                           | Linux, MacOS, Windows               | Linux, MacOS, Windows               |
| **Architecture**               | AMD64, ARM64, ARMv7, ppc64, S390x                                                               | AMD64, ARM64                        | AMD64, ARM64,i386                   |
| **Runtime**                    | docker, cri-o, containerd                                                                       | docker, cri-o                       | docker, containerd                  |
| **Min resource req:  CPU/RAM** | 2CPU+/2GB                                                                                       | N/A                                 | 1CPU+/512Mb                         |
| **Automation**                 | Minikube supports wide range of features/addons. Setup can be customized using minikube config  | Cluster configuration file support. | Cluster configuration file support. |
| **Multi-Node**                 | Yes                                                                                             | Yes                                 | Yes                                 |
| **Multi-Cluster**              | Yes                                                                                             | Yes                                 | Yes                                 |

## Conclusion

Although minikube is a mature and well-documented tool that comes with a wide range of built-in features and extensions, it is not recommended for production usage. Instead, k3d appears to be a good lightweight Kubernetes deployment that can be used as a temporary solution to speed up the product delivery process. It has fast node provisioning, supports multiple nodes, and allows the customization of cluster setup through config files.