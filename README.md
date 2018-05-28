# kubernetes-ansible

#### Disclaimer
Not for production use and not officially supported.
Ansible scripts work on Redhat/CentOS 7.x only.
Please note that deployment using these ansible scripts result in default passwords!

#### Pre-requisites
```
yum install -y git ansible
```

##### Clone the project
```
git clone https://github.com/mkieboom/kubernetes-ansible
cd kubernetes-ansible
```

#### Configuration
Specify the below configuration parameters
```
vi group_vars/all
```

# Allow running pods on master (yes/no=default)
allow_pods_on_master: 'no'

# Deploy demo environment settings, not for production environments! (yes/no=default)
demo_environment: 'no'

#### Node Configuration
Specify the node IP addresses or hostnames in the appropriate myhosts file, eg:
```
vi myhosts/1node_cluster
```
or:
```
vi myhosts/3node_cluster
```


#### Launch Ansible scripts:
Example playbook command deploying a single node K8S environment allowing pods on master and no login required (not for production environments!):
```
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook -i myhosts/1node_cluster cluster-minimum.yml -e "allow_pods_on_master=yes" -e "demo_environment=yes"
```
Example playbook command deploying a 3 node K8S environment not allowing pods on master (not for production environments!):
```
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook -i myhosts/3node_cluster cluster-minimum.yml
```

#### Supported OS

* Redhat 7 or higher
* CentOS 7 or higher
