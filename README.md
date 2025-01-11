I will use newest version of k8s v1.32

New criteria coming in 2025. 

https://github.com/cncf/curriculum/blob/master/CKA_Curriculum%20Coming%20Soon%20Q1%202025.pdf

(how to tell what init cgroup was used for the vms
ps -p 1)

by default after 1.22 kubelet defaults to use systemd but the container run time needs it set

sudo mkdir /etc/containerd/
containerd config default | sed 's/SystemdCgroup = false/SystemdCgroup = true/' | sudo tee /etc/containerd/config.toml
sudo systemctl restart containerd