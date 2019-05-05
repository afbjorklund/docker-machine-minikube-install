# DEPRECATED

_The "**localkube**" bootstrapper for Minikube has not been updated since [k8s](https://kubernetes.io) -1.10 (2018)._
_Instead it is now using the official Kubernetes "**kubeadm**" bootstrapper, and up to 1.14_

_If you want an installation like this one with a smaller footprint, look at [k3s](https://k3s.io) 1.13+ (2019)._
_It can be used both with **Docker Machine** ([containerd](https://containerd.io/)) or with **Podman Machine** ([cri-o](https://cri-o.io/))_

---

# Docker Machine - Kubernetes Minikube #

This sets up a single-node Kubernetes installation, using the regular Boot2Docker ISO.

Tested with minikube version: v0.26.0 (latest) and kubernetes version: v1.10.0 (stable)

Written by Anders Björklund (@afbjorklund)

## External URLs ##

Use `minikube-download` to get the binaries, and `minikube-install` to install into a machine.

The entire minikube installation procedure looks something like this: [machine-minikube.md](machine-minikube.md)

See https://github.com/kubernetes/minikube

## Requirements ##

It is _possible_ to install using the default 1 vCPU / 1G RAM, but 2 vCPU / 2G RAM is recommended.

The default installation is around 1G, but more disk space might be needed for swap and overhead.

Total download is around 270M, plus the container images.

### Kubernetes

    MINIKUBE_VERSION=0.26.0 # latest
    KUBERNETES_VERSION=v1.10.0 # $(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)

``` shell
curl -Lo minikube https://storage.googleapis.com/minikube/releases/$MINIKUBE_VERSION/minikube-linux-amd64 && chmod +x minikube
curl -Lo localkube https://storage.googleapis.com/minikube/k8sReleases/$KUBERNETES_VERSION/localkube-linux-amd64 && chmod +x localkube
curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$KUBERNETES_VERSION/bin/linux/amd64/kubectl && chmod +x kubectl
```

* 52M	kubectl
* 41M	minikube
* 174M	localkube


### Boot2Docker

The minikube installation scripts need bash (not just /bin/sh), so make sure that it is installed.

    # Boot2Docker ISO uses Tiny Core Linux 7.x
    http://repo.tinycorelinux.net/7.x/x86_64/tcz/

* 348K	bash.tcz
* 196K	ncurses.tcz
* 124K	readline.tcz

Certain addons, like `helm`, also requires that `socat` and `nsenter` (from util-linux) are available.

* 2.1M	openssl.tcz
* 152K	socat.tcz
* 1.1M	util-linux.tcz
