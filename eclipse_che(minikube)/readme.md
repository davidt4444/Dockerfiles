### install eclipse che
if kubectl not present 
#### install kubectl
https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-using-native-package-management

sudo apt-get update
// apt-transport-https may be a dummy package; if so, you can skip that package
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg

// If the folder `/etc/apt/keyrings` does not exist, it should be created before the curl command, read the note below.
// sudo mkdir -p -m 755 /etc/apt/keyrings
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.33/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
sudo chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg # allow unprivileged APT programs to read this keyring

// This overwrites any existing configuration in /etc/apt/sources.list.d/kubernetes.list
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.33/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo chmod 644 /etc/apt/sources.list.d/kubernetes.list   # helps tools such as command-not-found to work correctly

sudo apt-get update
sudo apt-get install -y kubectl

kubectl cluster-info

### install minikube if not already present
https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fdebian+package

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
sudo usermod -aG docker $USER && newgrp docker
sudo usermod -aG docker dathigp && newgrp docker
minikube start


if chectl is not present
#### installing chectl
https://eclipse.dev/che/docs/stable/administration-guide/installing-the-chectl-management-tool/

Run 
bash <(curl -sL  https://che-incubator.github.io/chectl/install.sh)
which chectl
chectl --version

#### install eclipse che
minikube start --addons=ingress,dashboard --vm=true --memory=10240 --cpus=4 --disk-size=50GB --kubernetes-version=v1.23.9
chectl server:deploy --platform minikube

chectl server:status

chectl dashboard:open
