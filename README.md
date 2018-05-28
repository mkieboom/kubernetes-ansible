# kubernetes-ansible

#### Disclaimer
Not for production use and not officially supported.
Ansible scripts work on Redhat/CentOS only.
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

# Allow running pods on master (true/false=default)
allow_pods_on_master: false

# Deploy demo environment settings, not for production environments! (true/false=default)
demo_environment: false



#### Launch Ansible scripts:
Example playbook command deploying a single secure node cluster with low memory config with no ecosystem packages:
```
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook -i myhosts/1node_cluster cluster-minimum.yml -e "memory=low" -e "secure=maprsasl"
```


#### Supported OS

* Redhat 7 or higher
* CentOS 7 or higher
