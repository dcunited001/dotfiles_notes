
# Go, Docker, Kubernetes, Minikube, Helm

### Install w/ Pacman

install these (or build from source with *-bin packages)

```
sudo pacman -Syu go \
  go-tools \
  docker \
  kubectx \
  kubectl \
  helm \
  minikube \
```

optionally, manually [rebuild go from
source](https://golang.org/doc/install/source) (requires go)

install from AUR

```
# docker-bin
# kubectl-bin
# minikube-bin

# kubelet-bin
# kubeadm-bin
# kubectl-trace-git
# cni-plugins-bin
```

## [Docker](https://wiki.archlinux.org/index.php/Docker) and Docker Hub

### Storage Root


The `--rbind` command is probably needed for layered docker images, for BTRFS
subvolumes. Found this script on an [IBM guide to using Docker in their
cloud](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.2.x/installing/docker_dir.html)

```bash
# remove all existing docker images ...
sudo docker rm -f $(docker ps -aq); docker rmi -f $(docker images -q)

sudo systemctl stop docker # if running
sudo rm -rf /var/lib/docker
sudo mkdir /var/lib docker 


sudo mkdir /
sudo mount --rbind /mnt/docker /var/lib/

```

then, make the mound permanent

```
/dev/sdx2 /var/lib/docker btrfs rw,noatime,compress=zstd:3,ssd,space_cache,autodefrag,commit=120,subvolid=256,subvol=/@ 0 0
```

## [Kubernetes](https://wiki.archlinux.org/index.php/Kubernetes)

- see [10 Kubernetes Best Practices (2020)](https://nirmata.com/2020/02/19/10-kubernetes-best-practices-you-can-easily-apply-to-your-clusters/)

### Kubectl, Kubeadm, CNI-Plugins

### Minikube

## Helm

## Go (from source)

```bash
export $LOCAL=~/.local
mkdir -p $LOCAL/src

# download a version of go for go-bootstrap
# wget -O go-bootstrap.tar.gz https://golang.org/dl/go1.15.3.linux.amd64.tar.gz

# or extract at the same time
wget -qO- https://golang.org/dl/go1.15.3.linux-amd64.tar.gz | tar -xzv - -C $LOCAL/src/

mv $LOCAL/src/go $LOCAL/src/go-bootstrap
git clone git@github.com:golang/go $LOCAL/go

# build and install
GOPATH=$LOCAL/go GOROOT_FINAL=/usr/local/go GOOS=linux GOROOT_BOOTSTRAP=$LOCAL/src/go-bootstrap/ ./all-bash

# move to $GOROOT_FINAL
sudo mkdir -p /usr/local
sudo mv $LOCAL/go /usr/local/go
sudo chown -R `whoami` /usr/local/go

# remake needed folders in $LOCAL/go
# - (i want bins installed outside /usr/local... i guess?)
mkdir /
```

#### Go Dependencies (for docker-bin)

standard go tools:

```bash
go get golang.org/x/tools/cmd/{bundle,callgraph,cover,digraph,compilebench,eg,fiximports,go-contrib-init,godex,godoc,goimports,gomvpkg,gorename,gotype,goyacc,guru,html2article,present,ssadump,stringer,toostash}

go get -u github.com/cpuguy83/go-md2man
```


