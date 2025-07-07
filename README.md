# Kubernetes Cluster with Vagrant

This project automates the creation of a multi-node Kubernetes cluster using Vagrant and VirtualBox. It provisions one master and two worker nodes running Ubuntu 24.04 ARM64, with all necessary dependencies and configurations handled by shell scripts.

## Features

- Automated provisioning of Kubernetes master and worker nodes
- Disk resizing and system preparation
- Automated installation of container runtime and Kubernetes components
- SSH key setup and IPv6 disabling
- Easy restoration of Vagrant boxes

## Requirements

- [Vagrant](https://www.vagrantup.com/) (with vagrant-disksize plugin)
- [VirtualBox](https://www.virtualbox.org/)
- Host system supporting ARM64 VMs (Apple Silicon recommended)

## Usage

1. **Clone this repository:**
   ```sh
   git clone <repo-url>
   cd kuber
   ```
2. **(Optional) Restore Vagrant boxes:**
   If you have `.box` files for the VMs, run:

   ```sh
   sudo ./restore_vagrant.sh
   ```

   This will add the boxes and bring up the VMs.

3. **Start the cluster:**

   ```sh
   vagrant up
   ```

   This will provision:

   - `kube-master1` (master node)
   - `kube-worker1` (worker node)
   - `kube-worker2` (worker node)

4. **Access the nodes:**
   ```sh
   vagrant ssh kube-master1
   vagrant ssh kube-worker1
   vagrant ssh kube-worker2
   ```

## Project Structure

- **Vagrantfile**: Defines the three VMs (1 master, 2 workers), their resources, networks, and provisioning scripts.
- **control_node.sh**: Prepares the control node (master) and pulls Kubernetes images.
- **disk_resize.sh**: Automatically resizes the VM disk, physical volume, logical volume, and filesystem to use all available space.
- **install_kubeadm.sh**: Installs containerd, Kubernetes components (kubeadm, kubelet, kubectl), configures system settings, disables swap and IPv6, and sets up SSH keys.
- **restore_vagrant.sh**: Adds Vagrant boxes from local `.box` files and brings up the VMs.

## Notes

- All scripts require root privileges. Use `sudo` when running them manually.
- Logs are stored in `$HOME/LOGS/global_env_config.log` on each VM.
- The default SSH public key is hardcoded in `install_kubeadm.sh`. Update it if needed.
- The project is designed for educational and development purposes.

## Credits

Developed by Dmitri Donskoy
