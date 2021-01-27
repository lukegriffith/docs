# Install kubernetes components

```bash
# add keys
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg  | sudo apt-key add -

# setup apt repos
cat <<EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF

sudo apt-get update

# find versions
apt-cache madison kubeadm | head -n 1
apt-cache madison kubelet | head -n 1
apt-cache madison kubectl | head -n 1

# install said versions
sudo apt-get install -y kubelet=1.20.2-00 kubeadm=1.20.2-00 kubectl=1.20.2-00

# hold
sudo apt-mark hold kubelet kubeadm kubectl
```

# Initialize the Control Plane

```
 sudo kubeadm init --pod-network-cidr=10.0.0.0/16 \
 sudo swapoff -a
 sudo kubeadm init --pod-network-cidr=10.0.0.0/16 \
 mkdir -p $HOME/.kube
 sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
 sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
