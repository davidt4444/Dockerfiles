### install eclipse che
https://eclipse.dev/che/docs/stable/administration-guide/installing-che-on-red-hat-openshift-local/

if kubectl or openshift not present go to openshift folder
Continue with the rest in the crc folder for openshift

if chectl is not present
#### installing chectl
https://eclipse.dev/che/docs/stable/administration-guide/installing-the-chectl-management-tool/

Run 
bash <(curl -sL  https://che-incubator.github.io/chectl/install.sh)
which chectl
chectl --version

#### install eclipse che
eval $(./crc oc-env)
oc login -u kubeadmin https://api.crc.testing:6443

chectl server:deploy --platform openshift
chectl server:start
chectl server:status
chectl dashboard:open

To remove
chectl server:delete
