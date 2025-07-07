# 🚀 Kubernetes Cluster with Vagrant

[![Vagrant](https://img.shields.io/badge/Vagrant-2.4.1-blue?logo=vagrant)](https://www.vagrantup.com/)
[![VirtualBox](https://img.shields.io/badge/VirtualBox-7.0-blue?logo=virtualbox)](https://www.virtualbox.org/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-1.30-blue?logo=kubernetes)](https://kubernetes.io/)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-orange?logo=ubuntu)](https://ubuntu.com/)

> **Easily spin up a multi-node Kubernetes cluster for development and testing using Vagrant and VirtualBox.**

---

## ✨ Features

- ⚡ **Automated provisioning** of Kubernetes master and worker nodes
- 💾 **Disk resizing** and system preparation
- 🐳 **Container runtime & Kubernetes install**
- 🔑 **SSH key setup** and 🔒 **IPv6 disabling**
- ♻️ **Easy restoration** of Vagrant boxes

---

## 🛠️ Requirements

- [Vagrant](https://www.vagrantup.com/) (with vagrant-disksize plugin)
- [VirtualBox](https://www.virtualbox.org/)
- Host system supporting ARM64 VMs (Apple Silicon recommended)

---

## 🚦 Quick Start

```bash
# 1. Clone this repository
$ git clone <repo-url>
$ cd kuber

# 2. (Optional) Restore Vagrant boxes from .box files
$ sudo ./restore_vagrant.sh

# 3. Start the cluster
$ vagrant up

# 4. Access the nodes
$ vagrant ssh kube-master1
$ vagrant ssh kube-worker1
$ vagrant ssh kube-worker2
```

---

## 🗂️ Project Structure

| File/Dir             | Description                                                                   |
| -------------------- | ----------------------------------------------------------------------------- |
| `Vagrantfile`        | 🏗️ Defines 1 master & 2 worker VMs, resources, networks, provisioning scripts |
| `control_node.sh`    | 🎛️ Prepares the control node (master), pulls Kubernetes images                |
| `disk_resize.sh`     | 📏 Resizes VM disk, PV, LV, and filesystem to use all available space         |
| `install_kubeadm.sh` | 🛠️ Installs containerd, kubeadm, kubelet, kubectl, disables swap/IPv6, SSH    |
| `restore_vagrant.sh` | ♻️ Adds Vagrant boxes from `.box` files and brings up the VMs                 |

---

## 📝 Notes

- 🔐 **Root required:** All scripts require root privileges. Use `sudo` when running manually.
- 🗃️ **Logs:** Stored in `$HOME/LOGS/global_env_config.log` on each VM.
- 🗝️ **SSH Key:** Default public key is hardcoded in `install_kubeadm.sh`. Update if needed.
- 🧪 **Intended for:** Educational and development use.

---

## 👨‍💻 Author

Developed by **Dmitri Donskoy**
