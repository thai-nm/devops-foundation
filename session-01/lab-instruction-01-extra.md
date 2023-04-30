# Lab 01: Extra - Set up Kubernetes cluster with kubeadm

## Pre-requisite

- ubuntu with systemd

step:
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

- Common settings for Kubernetes nodes:

  ```bash
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
  wget https://github.com/containerd/containerd/releases/download/v1.7.0/containerd-1.7.0-linux-amd64.tar.gz
  tar Cxzvf /usr/local containerd-1.7.0-linux-amd64.tar.gz

  wget -O /usr/local/lib/systemd/system/containerd.service https://raw.githubusercontent.com/containerd/containerd/main/containerd.service

  systemctl daemon-reload
  systemctl enable --now containerd
  
  # Install `runc`
  wget https://github.com/opencontainers/runc/releases/download/v1.1.7/runc.amd64
  install -m 755 runc.amd64 /usr/local/sbin/runc

  # Install CNI plugins
  mkdir -p /opt/cni/bin
  wget https://github.com/containernetworking/plugins/releases/download/v1.2.0/cni-plugins-linux-amd64-v1.2.0.tgz
  tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.2.0.tgz
  ```

- Configure `systemd` cgroup driver by setting `SystemdCgroup` in `/etc/containerd/config.toml` to `true`:
  ```toml
  [plugins."io.containerd.grpc.v1.cri".containerd.runtimes.runc]
  ...
  [plugins."io.containerd.grpc.v1.cri".containerd.runtimes.runc.options]
    SystemdCgroup = true
  ```

- Apply new driver configuration:
  ```bash
  sudo systemctl restart containerd
  ```
