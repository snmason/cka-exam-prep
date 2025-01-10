I will use newest version of k8s v1.32

New criteria coming in 2025. 

https://github.com/cncf/curriculum/blob/master/CKA_Curriculum%20Coming%20Soon%20Q1%202025.pdf


Install requirements:

sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl gpg
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.32/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.32/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl

sudo apt install -y containerd

(how to tell what init cgroup was used for the vms
ps -p 1)

by default after 1.22 kubelet defaults to use systemd but the container run time needs it set

sudo mkdir /etc/containerd/
containerd config default | sed 's/SystemdCgroup = false/SystemdCgroup = true/' | sudo tee /etc/containerd/config.toml
sudo systemctl restart containerd