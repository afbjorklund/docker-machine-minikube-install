# Docker Machine - Kubernetes Minikube #

This sets up a single-node Kubernetes installation, using the regular Boot2Docker ISO.

Tested with minikube version: v0.24.0 (latest) and kubernetes version: v1.8.0 (stable)

Written by Anders Björklund (@afbjorklund)

## External URLs ##

Use `minikube-download` to get the binaries, and `minikube-install` to install into a machine.

The entire minikube installation procedure looks something like this: [machine-minikube.md](machine-minikube.md)

See https://github.com/kubernetes/minikube

### Kubernetes

    MINIKUBE_VERSION=latest
    KUBERNETES_VERSION=$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)

``` shell
curl -Lo minikube https://storage.googleapis.com/minikube/releases/$MINIKUBE_VERSION/minikube-linux-amd64 && chmod +x minikube
curl -Lo localkube https://storage.googleapis.com/minikube/k8sReleases/$KUBERNETES_VERSION/localkube-linux-amd64 && chmod +x localkube
curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$KUBERNETES_VERSION/bin/linux/amd64/kubectl && chmod +x kubectl
```

* 50M	kubectl
* 40M	minikube
* 149M	localkube

### Boot2Docker

    # Boot2Docker ISO uses Tiny Core Linux 7.x
    http://repo.tinycorelinux.net/7.x/x86_64/tcz/

* 348K	bash.tcz
* 196K	ncurses.tcz
* 124K	readline.tcz

