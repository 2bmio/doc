---
title: 03. INSTALLATION AND CONFIGURATION
description: 
published: true
date: 2020-12-26T01:18:34.547Z
tags: 
editor: markdown
dateCreated: 2020-06-04T23:43:46.940Z
---

# 03. INSTALLATION AND CONFIGURATION
Your content here

## multipass
### install

```
# macos
brew cask install multipass

# linux fedora/arch/ubuntu

	# prepare for use snap
sudo dnf install snapd
sudo ln -s /var/lib/snapd/snap /snap

	# install using snap
sudo snap install multipass --classic

	# fix user permissions
sudo chown $USER:$USER /var/snap/multipass/common/multipass_socket

	# get info about multipass
snap info multipass
```

### commands

```
# launch:

## single instance
multipass launch --name k8s-182-AllTheWay --mem 8G --disk 40G

## multinode 
multipass launch --name k8s-18-master-1 --mem 2G --disk 20G
multipass launch --name k8s-18-master-2 --mem 2G --disk 20G
multipass launch --name k8s-18-master-3 --mem 2G --disk 20G
multipass launch --name k8s-18-worker-1 --mem 2G --disk 10G
multipass launch --name k8s-18-worker-2 --mem 2G --disk 10G
multipass launch --name k8s-18-worker-3 --mem 2G --disk 10G

# getting on
multipass list
multipass shell k8s-18-AllTheWay
multipass shell k8s-18-master-1

## using classic ssh with key
### copy the new key to user path
sudo cp /var/snap/multipass/common/data/multipassd/ssh-keys/id_rsa ~/.ssh/id_mpss
### change permissions
sudo chown $USER:$USER ~/.ssh/id_mpss
### connect
ssh ubuntu@<multipass-ip> -i ~/.ssh/id_mpss
```


## microk8s
https://microk8s.io/docs/release-notes


### install
```
# get available list for microk8s
snap info microk8s

sudo snap install microk8s --classic
sudo snap install microk8s --classic --channel=1.16/stable

sudo usermod -a -G microk8s $USER
sudo iptables -P FORWARD ACCEPT


#---------------------------------------------

# # # # # # # # # # # # # # # # 
#    KUBECTL
# # # # # # # # # # # # # # # # 

# get available list for kubectl
snap info kubectl

sudo snap install kubectl --classic
sudo snap install kubectl --classic --channel=1.16/stable

# logout
mkdir ~/.kube
microk8s.kubectl config view --raw > $HOME/.kube/config

```

### commands

```
microk8s.kubectl get nodes
microk8s.add-node
  ubuntu@k8s-master:~$ microk8s.add-node
  Join node with: microk8s.join 192.168.64.3:25000/GdnlcwJRAWzigHhodFPmFTIMQHgrSCIZ

microk8s.status
microk8s.enable --help
microk8s.enable dns storage dashboard


# old way → microk8s.enable dns dashboard ingress helm

## List of the most important addons

*   dns: Deploy DNS. This addon may be required by others, thus we recommend you always enable it.
*   dashboard: Deploy kubernetes dashboard as well as grafana and influxdb.
*   storage: Create a default storage class. This storage class makes use of the hostpath\-provisioner pointing to a directory on the host.
*   ingress: Create an ingress controller.
*   gpu: Expose GPU(s) to MicroK8s by enabling the nvidia\-docker runtime and nvidia\-device\-plugin\-daemonset. Requires NVIDIA drivers to be already installed on the host system.
*   istio: Deploy the core Istio services. You can use the `microk8s.istioctl` command to manage your deployments.
*   registry: Deploy a docker private registry and expose it on localhost:32000. The storage addon will be enabled as part of this addon.

microk8s.kubectl -n kube-system get secret

microk8s.kubectl -n kube-system describe secret kubernetes-dashboard-token-XXXXX

microk8s.kubectl port-forward -n kube-system service/kubernetes-dashboard 10443:443 --address 0.0.0.0

https://[microk8s-master-ip]:10443
```


## k0s
https://k0sproject.io/


### install

```

curl -sSLf https://get.k0s.sh | sh

mkdir /root/bin/
curl -sSLf https://github.com/k0sproject/k0s/releases/download/v0.9.0/k0s-v0.9.0-amd64 > /root/bin/k0s
chmod 755 /root/bin/k0s


sudo curl --output /usr/local/sbin/kubectl -L "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"



sudo chmod +x /usr/local/sbin/kubectl
sudo chmod +x /root/bin/k0s

mkdir -p ${HOME}/.k0s
k0s default-config | tee ${HOME}/.k0s/k0s.yaml

mkdir -p ${HOME}/.k0s/libexec
export KUBECONFIG="${HOME}/.k0s/kubeconfig"
kubectl get pods --all-namespaces


flexVolumeDriverPath: /root/.k0s/libexec/k0s/kubelet-plugins/volume/exec/nodeagent~uds
volumePluginDir
k0s server -c ${HOME}/.k0s/k0s.yaml --enable-worker &



k0s token create --role=worker
k0s worker "long-join-token"

```

