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
<img width="1158" alt="image" src="https://user-images.githubusercontent.com/117667360/216758838-abb41e53-088b-45a6-a5e0-b63266717c4c.png">

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
nano inventory\mycluster\group_vars\k8s_cluster\addons.yml
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
nano inventory\mycluster\group_vars\k8s_cluster\k8s-cluster.yml
```
```
kube_proxy_strict_arp: true
```
* ### [Install Docker](https://docs.docker.com/engine/install/ubuntu/)

* ### Run execute container
* ### Go to kubespray folder and start ansible-playbook
* ### Connect to VM and copy kubectl configuration file
