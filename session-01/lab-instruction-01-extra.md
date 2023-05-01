# Lab 01: Extra - Set up Kubernetes cluster with kubeadm

## Pre-requisite

- Linux VM with:
  -  At least 4GB of memory and 2 vCPU
  -  Internet access

## Instruction
To bootstrap a Kubernetes cluster with `kubeadm`, the following steps should be performed:
- Install `kubeadm`, `kubelet`, `kubectl`:
  - `kubeadm`: administration tool to initiate Kubernetes cluster
  - `kubelet`: Linux process run as a `systemd` service to manage pods on a node
  - `kubectl`: client tool to communicate with Kubernetes cluster
- Prepare common settings for Kubernetes nodes
- Prepare `containerd` container runtime:
  - `containerd`: container runtime in charge of creating containers based on requirements received from `kubelet`.
- Boostrap a Kubernetes cluster with `kubeadm`
- Install `flannel` container network interface or CNI
- Create a simple pod


Below are detailed instructions:
- Install `kubeadm`, `kubectl`, `kubelet`:
  ```bash
  # Update `apt` package manager and install dependencies:
  sudo apt-get update
  sudo apt-get install -y apt-transport-https ca-certificates curl

  # Download Google public signing key:
  sudo curl -fsSLo /etc/apt/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg

  # Add `Kubernetes` repository:
  echo "deb [signed-by=/etc/apt/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

  # Update `apt` package manager and install tools:
  sudo apt-get update
  sudo apt-get install -y kubelet kubeadm kubectl
  sudo apt-mark hold kubelet kubeadm kubectl
  ```

  NOTE: `/etc/apt/keyrings` directory might not exist, create one if you need to and make it world-readable but writable only by admins.

- Prepare common settings for Kubernetes nodes:

  ```bash
  # These settings should be OK without any issues
  cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
  overlay
  br_netfilter
  EOF

  sudo modprobe overlay
  sudo modprobe br_netfilter

  # sysctl params required by setup, params persist across reboots
  cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
  net.bridge.bridge-nf-call-iptables  = 1
  net.bridge.bridge-nf-call-ip6tables = 1
  net.ipv4.ip_forward                 = 1
  EOF

  # Apply sysctl params without reboot
  sudo sysctl --system

  # Verify that the br_netfilter, overlay modules are loaded
  lsmod | grep br_netfilter
  lsmod | grep overlay
  sysctl net.bridge.bridge-nf-call-iptables net.bridge.bridge-nf-call-ip6tables net.ipv4.ip_forward
  ```

- Prepare `containerd` container runtime:
  ```bash
  # Download `container` binary file
  wget https://github.com/containerd/containerd/releases/download/v1.7.0/containerd-1.7.0-linux-amd64.tar.gz
  sudo tar Cxzvf /usr/local containerd-1.7.0-linux-amd64.tar.gz

  # Download `containerd` service file and use `systemctl` to manage `containerd` service
  sudo mkdir -p /usr/local/lib/systemd/system
  sudo wget -O /usr/local/lib/systemd/system/containerd.service https://raw.githubusercontent.com/containerd/containerd/main/containerd.service

  systemctl daemon-reload
  systemctl enable --now containerd
  
  # Install `runc`, a dependency required by `containerd`
  wget https://github.com/opencontainers/runc/releases/download/v1.1.7/runc.amd64
  sudo install -m 755 runc.amd64 /usr/local/sbin/runc

  # Install CNI plugins, a denpendency required by `containerd` so that it can work with other CNI add-ons.  
  sudo mkdir -p /opt/cni/bin
  wget https://github.com/containernetworking/plugins/releases/download/v1.2.0/cni-plugins-linux-amd64-v1.2.0.tgz
  sudo tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.2.0.tgz

  # Generate default config file 
  sudo sh -c "containerd config default > /etc/containerd/config.toml"

  # Configure `systemd` cgroup driver by setting `SystemdCgroup` in `/etc/containerd/config.toml` to `true`:
  sudo sed -i 's:SystemdCgroup = false:SystemdCgroup = true:g' /etc/containerd/config.toml

  # Apply new driver configuration
  sudo systemctl restart containerd
  ```

- Boostrap Kubernetes cluster:
  ```bash
  # Boostrap our cluster, pod CIDR range of 10.244.0.0/16 is required by `flannel` CNI add-on below
  sudo kubeadm init --pod-network-cidr 10.244.0.0/16

  # Configure `kubectl` so that it can communicate with our created cluster
  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config
  ```

- Install `flannel` CNI add-on:
  ```bash
  kubectl apply -f https://github.com/flannel-io/flannel/releases/latest/download/kube-flannel.yml
  ```

- Clean up:
  ```bash
  kubectl drain <node name> --delete-emptydir-data --force --ignore-daemonsets
  sudo kudeadm reset
  sudo sh -c "iptables -F && iptables -t nat -F && iptables -t mangle -F && iptables -X"
  ```