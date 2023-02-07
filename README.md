# Homework 12 - Task3. K8S - Kubespray
## Task
#### 1. Create and configure VM:
> * Clone Kubespray release repository
> * Copy and edit inventory file
> * Turn on MetalLB
> * Run execute container
> * Go to kubespray folder and start ansible-playbook
> * Connect to VM and copy kubectl configuration file
#### 2. Install Ingress-controller
#### 3. Prepare domain name and Configure cert-manager
#### 4. Prepare Nginx deployment ( deployment, service, ingress )

# 1 Step: Create and configure VM
* VM on digitalocean with folliwing parameters:

* ### Clone Kubespray release repository:
```
git clone https://github.com/kubernetes-sigs/kubespray.git
cd kubespray
git checkout release-2.20
```
* ### Copy and edit inventory file
```
cp -rfp inventory/sample inventory/mycluster
nano inventory/mycluster/inventory.ini
```
<img width="1250" alt="image" src="https://user-images.githubusercontent.com/117667360/216760216-45ffe798-c5e4-47e7-81f1-0a222409027d.png">

* ### Turn on MetalLB

```
nano inventory/mycluster/group_vars/k8s_cluster/addons.yml
```
```
metallb_enabled: true
metallb_speaker_enabled: true
metallb_avoid_buggy_ips: true
metallb_ip_range:
  - "10.200.0.2/32"
# 10.200.0.2 VM private IP address
```

```
nano inventory/mycluster/group_vars/k8s_cluster/k8s-cluster.yml
```
```
kube_proxy_strict_arp: true
```
* ### [Install Docker](https://docs.docker.com/engine/install/ubuntu/)

* ### Run execute container
```
docker run --rm -it -v /mnt/path/to/kubespray/Kubernetes2:/mnt \
  -v /home/user/path/to/ssh/keys/.ssh:/pem \
  quay.io/kubespray/kubespray:v2.20.0 bash
```

* ### Go to kubespray folder and start ansible-playbook
* ### Connect to VM and copy kubectl configuration file






```
nano inventory/mycluster/group_vars/k8s_cluster/addons.yml
```
<img width="1207" alt="image" src="https://user-images.githubusercontent.com/117667360/217276964-a1119a50-e89b-4efd-ac7e-9184ca439e08.png">

```
nano inventory/mycluster/group_vars/k8s_cluster/k8s-cluster.yml
```
<img width="1022" alt="image" src="https://user-images.githubusercontent.com/117667360/217277394-aa6d70fe-945f-43f8-8bc5-9f911459c61b.png">

```
docker run --rm -it -v /etc/:/mnt   -v /root/.ssh:/pem   quay.io/kubespray/kubespray:v2.20.0 bash
```

