### install openshift

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

#### install openshift
https://console.redhat.com/openshift/create/local
download tarball
cp ~/Downloads/crc-linux-amd64.tar.xz .
If you don't have xz
sudo apt install xz-utils
tar -xvf crc-linux-amd64.tar.xz
cd crc-linux-2.49.0-amd64/
If you have a vpn on the server that runs on 10.0.0.x
sudo systemctl stop openvpn@myserver
sudo systemctl stop openvpn

For repeats the next two commands
./crc delete -f
./crc cleanup

Finally the setup
./crc setup
./crc daemon
Make sure to sub the full path of the pull-secret below
./crc start --memory 12288 --disk-size=64 --pull-secret-file /home/dathigp/Downloads/pull-secret.txt

To stop the cluster
./crc stop

##### Problems you might face
If you get can't connect a quick fix might be 
kubectl proxy --port=8080 &
To spawn on that port if unavailable

If you get something about kvm_amd not loading 
In the bios->Security->System security->enable virtualization
Make a note in the logs so that someone doesn't try to use a software removal tool instead of the proper uninstall +|-(*)-|-

To logout from terminal if normal process doesn't work
sudo shutdown -r now 
or
sudo pkill -u username

If it is an error for missing virtiofsd
sudo apt install virtiofsd
sudo apt install virt-manager

If it is failing on copying the pull-secret (Try restart or log off first) or any number of other errors that stopping and starting don't solve, redownload the crc executable and 
sudo rm -r ~/.crc
and go back to the beginnning

