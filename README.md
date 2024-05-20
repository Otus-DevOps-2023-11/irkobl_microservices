# 28.Введение в Kubernetes #1

    Выполня развертывание на своих серверах, использовался Proxmox. Так как не оплачен YandexCloud. 

    Ниже весь набор комманд для мастер ноды ниже. 

```bash
   34  cat /etc/os-release 
   35  wget https://github.com/Mirantis/cri-dockerd/releases/download/v0.3.12/cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb
   36  ls
   37  sudo dpkg -i cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb 
   38  ls
   39  wget https://github.com/containerd/containerd/releases/download/v1.7.15/containerd-1.7.15-linux-amd64.tar.gz
   40  ls
   41  sudo tar Cxzvf /usr/local containerd-1.7.15-linux-amd64.tar.gz 
   42  systemctl daemon-reload
   43  sudo systemctl daemon-reload
   44  sudo systemctl enable --now containerd
   45  wget https://raw.githubusercontent.com/containerd/containerd/main/containerd.service
   46  ls
   47  systemctl status ssh
   48  sudo mv containerd.service /lib/systemd/system/
   49  sudo systemctl daemon-reload
   50  sudo systemctl enable --now containerd
   51  wget https://github.com/opencontainers/runc/releases/download/v1.1.12/runc.amd64
   52  ls
   53  install -m 755 runc.amd64 /usr/local/sbin/runc
   54  sudo install -m 755 runc.amd64 /usr/local/sbin/runc
   55  wget https://github.com/containernetworking/plugins/releases/download/v1.4.1/cni-plugins-linux-amd64-v1.4.1.tgz
   56  sudo mkdir -p /opt/cni/bin
   57  tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.4.1.tgz 
   58  sudo tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.4.1.tgz 
   59  ls
   60  dpkg -i cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb 
   61  sudo dpkg -i cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb 
   62  containerd
   63  sudo dpkg -i cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb 
   64  containerd -v
   65  iptables
   66  sudo apt install iptables -y
   67  systemctl
   68  systemctl status containerd
   69  sudo apt install iptables -y
   70  $ curl -O https://download.docker.com/linux/debian/dists/bookworm/pool/stable/amd64/containerd.io_1.6.28-2_amd64.deb
   71  curl -O https://download.docker.com/linux/debian/dists/bookworm/pool/stable/amd64/containerd.io_1.6.28-2_amd64.deb
   72  wget https://download.docker.com/linux/debian/dists/bookworm/pool/stable/amd64/containerd.io_1.6.28-2_amd64.deb
   73  sudo apt install ./containerd.io_1.6.28-2_amd64.deb 
   74  sudo systemctl stop containerd
   75  sudo apt install ./containerd.io_1.6.28-2_amd64.deb 
   76  sudo apt-get install ./containerd.io_1.6.28-2_amd64.deb 
   77  sudo apt-cache search libltdl7
   78  apt-get install libltdl7 libltdl7-dev
   79  sudo apt-get install libltdl7 libltdl7-dev
   80  sudo apt-get --fix-broken install libltdl7 libltdl7-dev
   81  sudo apt-get install libltdl7 libltdl7-dev
   82  sudo apt-get update
   83  sudo apt-get install libltdl7 libltdl7-dev
   84  nano /etc/apt/sources.list.d/docker.list
   85  nano /etc/apt/sources.list.d/
   86  for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
   87  sudo for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
   88  for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
   89  sudo ls /etc/apt/sources.list.d/
   90  sudo nano /etc/apt/sources.list
   91  sudo apt-get install ca-certificates curl
   92  dpkg list
   93  dpkg --list
   94  ls
   95  dpkg remove cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb
   96  dpkg 
   97  dpkg --help
   98  dpkg -r cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb
   99  sudo dpkg -r cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb
  100  sudo dpkg --remove cri-dockerd_0.3.12.3-0.debian-bookworm_amd64.deb
  101  dpkg --help
  102  dpkg -l | grep cri-dockerd
  103  sudo dpkg -r cri-dockerd
  104  sudo apt-get install ca-certificates curl
  105  sudo apt install libltdl7 libltdl7-dev
  106  apt-cache search pigz
  107  sudo apt-cache search pigz
  108  sudo apt install pigz
  109  sudo apt-cache search cgroup-lite
  110  sudo apt-cache search cgroup
  111  sudo apt install cgroup-tools cgroupfs-mount
  112  sudo apt-cache search aufs-tools 
  113  sudo apt-cache search aufs
  114  sudo apt-cache search iptables
  115  sudo apt install iptables -y
  116  ls
  117  sudo dpkg -i *.deb
  118  sudo apt update -qq && sudo apt install -y    btrfs-tools   containers-common   git   libassuan-dev              libdevmapper-dev   libglib2.0-dev   libc6-dev   libgpgme11-dev   libgpg-error-dev   libseccomp-dev   libsystemd-dev   libbtrfs-dev   libselinux1-dev   pkg-config   go-md2man   cri-o-runc   libudev-dev   software-properties-common   gcc   make
  119  sudo apt-get update -qq && sudo apt-get install -y   libbtrfs-dev   containers-common   git   libassuan-dev   libdevmapper-dev   libglib2.0-dev   libc6-dev   libgpgme-dev   libgpg-error-dev   libseccomp-dev   libsystemd-dev   libselinux1-dev   pkg-config   go-md2man   cri-o-runc   libudev-dev   software-properties-common   gcc   make
  120  sudo echo 'deb http://deb.debian.org/debian buster-backports main' > /etc/apt/sources.list.d/backports.list
  121  echo 'deb http://deb.debian.org/debian buster-backports main' > /etc/apt/sources.list.d/backports.list
  122  sudo echo 'deb http://deb.debian.org/debian buster-backports main' > /etc/apt/sources.list.d/backports.list
  123  sudo -i
  124  sudo apt update
  125  apt install -y -t buster-backports libseccomp2 || apt update -y -t buster-backports libseccomp2
  126  sudo apt install -y -t buster-backports libseccomp2 || sudo apt update -y -t buster-backports libseccomp2
  127  sudo apt update
  128  sudo rm -rf /etc/apt/sources.list.d/backports.list
  129  sudo  apt update
  130  sudo apt-cache search cri-o
  131  sudo for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
  132  for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
  133  sudo apt-get update
  134  sudo cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
  135  overlay
  136  br_netfilter
  137  EOF
  138  sudo modprobe overlay
  139  sudo modprobe br_netfilter
  140  sudo cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
  141  net.bridge.bridge-nf-call-iptables  = 1
  142  net.bridge.bridge-nf-call-ip6tables = 1
  143  net.ipv4.ip_forward                 = 1
  144  EOF
  145  sudo sysctl --system
  146  sudo lsmod | grep br_netfilter
  147  lsmod | grep overlay
  148  sudo sysctl net.bridge.bridge-nf-call-iptables net.bridge.bridge-nf-call-ip6tables net.ipv4.ip_forward
  149  sudo apt-get install ca-certificates curl
  150  sudo install -m 0755 -d /etc/apt/keyrings
  151  sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
  152  sudo chmod a+r /etc/apt/keyrings/docker.asc
  153  (. /etc/os-release && echo "$VERSION_CODENAME")
  154  echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  155    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  156  sudo apt-get update
  157  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  158  sudo apt-get update
  159  sudo apt-get install -y apt-transport-https ca-certificates curl gpg
  160  curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
  161  echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
  162  sudo apt-get update
  163  sudo apt-get install -y kubelet kubeadm kubectl
  164  sudo apt-mark hold kubelet kubeadm kubectl
  165  ls
  166  nano kubeadm-config.yaml
  167  kubeadm init --config kubeadm-config.yaml
  168  kubeadm version
  169  kubectl 
  170  kubectl vrsion
  171  kubectl version
  172  kubelet version
  173  kubelet
  174  sudo kubelet
  175  kubeadm
  176  kubeadm version
  177  kubeadm init --config kubeadm-config.yaml
  178  systemctl daemon-reload
  179  sudo systemctl daemon-reload
  180  sudo systemctl restart kubelet
  181  ls
  182  nano kubeadm-config.yaml 
  183  kubeadm init --config kubeadm-config.yaml
  184  sudo kubeadm init --config kubeadm-config.yaml
  185  sudo sudo swapoff -a
  186  sudo nano /etc/fstab
  187  systemctl | grep systemd.swap
  188  reboot
  189  sudo kubeadm init --config kubeadm-config.yaml
  190  systemctl
  191  sudo systemctl status cri-docker.socket
  192  sudo groupadd docker
  193  sudo systemctl status cri-docker.socket
  194  sudo usermod -aG cri-docker $USER
  195  sudo usermod -aG docker $USER
  196  sudo systemctl restart cri-docker.socket
  197  sudo systemctl status cri-docker.socket
  198  sudo kubeadm init --config kubeadm-config.yaml
  199  nano kubeadm-config.yaml 
  200  sudo kubeadm init --config kubeadm-config.yaml
  201  nano kubeadm-config.yaml 
  202  sudo kubeadm init --config kubeadm-config.yaml
  203  nano kubeadm-config.yaml 
  204  sudo kubeadm init --config kubeadm-config.yaml
  205  sudo kubeadm init --help
  206  ip add
  207  sudo kubeadm init --config kubeadm-config.yaml 
  208  sudo kubeadm init --config kubeadm-config.yaml --cri-socket /var/run/cri-dockerd.sock
  209  ls
  210  sudo kubeadm init --config kubeadm-config.yaml --cri-socket /var/run/cri-dockerd.sock 
  211  sudo kubeadm init --config kubeadm-config.yaml --cri-socket '/var/run/cri-dockerd.sock' 
  212  nano kubeadm-config.yaml 
  213  sudo kubeadm init --config kubeadm-config.yaml 
  214  sudo kubeadm init --config kubeadm-config.yaml --cri-socket '/var/run/cri-dockerd.sock' 
  215  sudo kubeadm init kubeadm-config.yaml --cri-socket /var/run/cri-dockerd.sock 
  216  sudo kubeadm init --cri-socket /var/run/cri-dockerd.sock 
  217  sudo kubeadm init --config kubeadm-config.yaml
  218  ls -alh
  219  ls
  220  sudo kubeadm init --config kubeadm-config.yaml
  221  nano kubeadm-config.yaml 
  222  nano etc/kubernetes/admin.conf
  223  sudo -i
  224  nano kubeadm-config.yaml 
  225  sudo kubeadm init --config kubeadm-config.yaml 
  226  sudo kubeadm init --config kubeadm-config.yaml
  227  ping 8.8.8.8
  228  sudo kubeadm reset
  229  ls
  230  sudo kubeadm init --config kubeadm-config.yaml
  231  sudo kubeadm reset --
  232  history | grep kubea
  233  sudo kubeadm reset --cri-socket /var/run/cri-dockerd.sock
  234  ls /var/run/
  235  sudo kubeadm init --config kubeadm-config.yaml
  236  kubectl get nodes
  237  ip route show
  238  mkdir -p $HOME/.kube
  239  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  240  sudo chown $(id -u):$(id -g) $HOME/.kube/config
  241  kubeadm token list
  242  kubeadm join 192.168.222.193:6443 --token xwggpe.0zffi9ul9yswnzl2         --discovery-token-ca-cert-hash sha256:d43a48ddcf657f0e8910ab0d78417dcff4b31e187c741a767b7c38a147f0b092
  243  sudo kubeadm join 192.168.222.193:6443 --token xwggpe.0zffi9ul9yswnzl2         --discovery-token-ca-cert-hash sha256:d43a48ddcf657f0e8910ab0d78417dcff4b31e187c741a767b7c38a147f0b092
  244  kubeadm join --help
  245  sudo kubeadm join 192.168.222.193:6443 --token xwggpe.0zffi9ul9yswnzl2         --discovery-token-ca-cert-hash sha256:d43a48ddcf657f0e8910ab0d78417dcff4b31e187c741a767b7c38a147f0b092
  246  sudo kubeadm join 192.168.222.193:6443 --token xwggpe.0zffi9ul9yswnzl2  cri-socket unix:///var/run/cri-dockerd.sock         --discovery-token-ca-cert-hash sha256:d43a48ddcf657f0e8910ab0d78417dcff4b31e187c741a767b7c38a147f0b092
  247  sudo kubeadm join 192.168.222.186:6443 --token xwggpe.0zffi9ul9yswnzl2  cri-socket unix:///var/run/cri-dockerd.sock --discovery-token-ca-cert-hash sha256:d43a48ddcf657f0e8910ab0d78417dcff4b31e187c741a767b7c38a147f0b092
  248  kubectl get nodes
  249  sudo kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.27.3/manifests/tigera-operator.yaml
  250  curl localhost:8080
  251  curl localhost:80
  252  sudo export KUBECONFIG=/etc/kubernetes/admin.conf
  253  export KUBECONFIG=/etc/kubernetes/admin.conf
  254  curl localhost:8080
  255  sudo kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.27.3/manifests/tigera-operator.yaml
  256  kubectl get nodes
  257  sudo kubectl get nodes
  258  kubectl get nodes
  259  sudo kubectl get nodes
  260  echo $KUBECONFIG
  261  sudo apt-get install ntp
  262  sudo apt-get install ntpdate
  263  sudo ntpdate ntp.ubuntu.com
  264  sudo kubectl get nodes
  265  kubectl get nodes
  266  kubectl describe node debian
  267  sudo kubeadm join 192.168.222.186:6443 --token xwggpe.0zffi9ul9yswnzl2  cri-socket unix:///var/run/cri-dockerd.sock --discovery-token-ca-cert-hash sha256:d43a48ddcf657f0e8910ab0d78417dcff4b31e187c741a767b7c38a147f0b092
  268  kubectl get nodes
  269  kubectl describe node debian
  270  sudo kubeadm join 192.168.222.186:6443 --token xwggpe.0zffi9ul9yswnzl2  cri-socket unix:///var/run/cri-dockerd.sock --discovery-token-ca-cert-hash sha256:d43a48ddcf657f0e8910ab0d78417dcff4b31e187c741a767b7c38a147f0b092
  271  kubectl get nodes
  272  kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.27.3/manifests/tigera-operator.yaml
  273  curl https://raw.githubusercontent.com/projectcalico/calico/v3.27.3/manifests/custom-resources.yaml -O
  274  kubectl create -f custom-resources.yaml
  275  ls
  276  nano custom-resources.yaml 
  277  watch kubectl get pods -n calico-system
  278  curl https://raw.githubusercontent.com/projectcalico/calico/v3.27.3/manifests/calico.yaml -O
  279  nano calico.yaml 
  280  vi calico.yaml 
  281  nano calico.yaml 
  282  kubectl apply -f calico.yaml
  283  watch kubectl get pods -n calico-system
  284  sudo kubectl apply -f calico.yaml
  285  kubectl apply -f calico.yaml
  286  watch kubectl get pods -n calico-system
  287  kubectl get nodes
  288  kubeadm token create --print-join-command
  289  history | grep kubeadm
  290  kubectl get nodes
  291  watch kubectl get pods -n calico-system
  292  nano post-deployment.yaml
  293  kubectl apply -f post-deployment.yaml 
  294  kubectl get pods
  295  cubectl describe post-deployment-68db465f9c-fhthw
  296  kubectl describe post-deployment-68db465f9c-fhthw
  297  kubectl describe pods
  298  ls /etc/kubernetes/ip add
  299  ip add
  300  ls /etc/kubernetes/ip add
  301  ls /etc/kubernetes/
  302  cp /etc/kubernetes/controller-manager.conf .
  303  sudo cp /etc/kubernetes/controller-manager.conf .
  304  sudo cp /etc/kubernetes/scheduler.conf .
  305  ls
  306  ls -alh
  307  chown debian:debian controller-manager.conf 
  308  sudo chown debian:debian controller-manager.conf 
  309  sudo chown debian:debian scheduler.conf 
  310  ls
  311  ls -alh
  312  q
  313  ls -alh .kube/
  314  nano .kube/config 
  315  ls /etc/kubernetes/
  316  nano /etc/kubernetes/admin.conf 
  317  sudo nano /etc/kubernetes/admin.conf 
  318  kubectl get pods
  319  kubectl describe pods
```
