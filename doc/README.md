## Software comparison

minikube - minikube is a Kubernetes SIGs project and has been started more than three years ago. It takes the approach of spawning a VM that is essentially a single node K8s cluster. Due to the support for a bunch of hypervisors it can be used on all of the major operating systems. This also allows you to create multiple instances in parallel.

kind (**K**ubernetes **in** **D**ocker) - Kind is another Kubernetes SIGs project but is quite different compared to minikube. As the name suggests it moves the cluster into Docker containers. This leads to a significantly faster startup speed compared to spawning VM.

k3d - K3s is a minified version of Kubernetes developed by Rancher Labs. By removing dispensable features (legacy, alpha, non-default, in-tree plugins) and using lightweight components (e.g. sqlite3 instead of etcd3) they achieved a significant downsizing. This results in a single binary with a size of around 60 MB.

| Tool | minikube | kind | k3d |
| ------------- |:-------------:|:-------------:|:-------------:|
| Supported OS and Architectures | OS: linux,windows,macos <br />  ARCH: amd64, arm, arm64, ppc64le, s390x.     |OS: linux,windows,macos. <br />  ARCH: amd64, arm64.     |OS: linux,windows,macos  <br /> ARCH: amd64, arm, arm64.  |
| Automation      | With additional package     | Available by default    | Auto deployment feature     |
| Features      | LoadBalancer, Multi-cluster , NodePorts - using minikube service, Persistent Volumes, Ingress, Dashboard, Container runtimes, Configure apiserver and kubelet options via command-line flags, Supports common CI environments     | Multi-node, Go packages implementing cluster creation, image build, etc., A command line interface (kind) built on these packages., Docker image(s) written to run systemd, Kubernetes, etc., kubetest integration also built on these packages (WIP)     |  Containerd & runc, Flannel for CNI, CoreDNS, Metrics Server, Traefik for ingress, Klipper-lb as an embedded service load balancer provider, Kube-router netpol controller for network policy, Helm-controller to allow for CRD-driven deployment of helm manifests, Kine as a datastore shim that allows etcd to be replaced with other databases, Local-path-provisioner for provisioning volumes using local storage, Host utilities such as iptables/nftables, ebtables, ethtool, & socat     |
| Pros      | Easy setup and management of a single-node and multi-node Kubernetes cluster. Support for multiple operating systems and architectures. Integration with kubectl for managing and interacting with the cluster. Optional add-ons to enhance cluster functionality. Ingress and load balancing support. Popularity, Community support and active development. Experimental Podman support.    | Lightweight and fast setup of Kubernetes clusters using Docker containers. Support for multiple operating systems and architectures. Full compatibility with the standard Kubernetes API and tools. Customization and extensibility of clusters through Kubernetes configuration. Suitable for local development, testing, and CI pipelines. Easy creation and deletion of clusters through the CLI. Podman support. yml-file for configuration.     | Lightweight and fast creation of Kubernetes clusters using Docker containers. Support for multiple operating systems and architectures. Integration with container runtimes like Docker and containerd. Customization and extensibility of clusters through Kubernetes configuration. Networking support for container communication within the cluster. Load balancer integration for exposing services. Suitable for local development, testing, and CI pipelines. yml-file for configuration.   |
| Cons      | Additional features like monitoring require integration with third-party tools. Resource-intensive, may require a machine with sufficient resources to run smoothly. Lack of built-in support for automatic cluster provisioning. Poor automation options: there is no configuration file.    | Lack of built-in monitoring or control features. Additional tools or integrations needed for monitoring and cluster management. Lack of automated cluster provisioning.   | Lack of built-in monitoring or control features. Additional tools or integrations needed for monitoring and cluster management. Lack of automated cluster provisioning. Cluster scalability may be limited based on machine resources and Docker license limitations. Podman is not supported.   |

## Demonstration

![demo](../img/task_4.gif)

## Results

One of the risks associated with Docker licensing is that Docker uses a dual open source license. Docker is distributed under the Apache 2.0 license, which allows the code to be freely used and modified. But Docker also uses the Docker Commercially Supported (CS) license, which requires users to pay for commercial use of Docker and receive support from Docker, Inc. This license does not allow you to freely use and modify Docker without paying an appropriate fee.
Also, Docker does not support all operating systems, which can be another risk. For example, Docker does not support Windows 7, which can cause problems for users using that OS.
One alternative to Docker is Podman, which is free and open source software under the Apache 2.0 license. The main advantage of Podman is that it does not require running as a service, making it safer to use in isolated environments. Also, Podman can run without additional privileges and does not require additional configuration to run in containers. In addition, Podman supports a wider range of operating systems and architectures, which gives greater flexibility in choosing an operating system for running containers.

Summing up, the following conclusions can be drawn:
1. All three tools (minikube, kind, k3d) support Linux, macOS, and Windows, as well as amd64 and arm64 architectures.
2. All three tools have the ability to automate and provide monitoring.
3. minikube and k3d have additional Kubernetes management features, while kind does not.
4. All three tools have documentation and community support.
5. kind and k3d have low complexity to set up and use, while minikube has moderate complexity.

Considering the advantages and disadvantages, it can be concluded that kind or k3d is the best to use for POC application deployment because they have low complexity of setup and use, as well as speed of deployment and stability of operation. I suggest using k3d to deploy the project.
