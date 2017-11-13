# Ansible Hadoop Core

This is a Ansible role to install Apache Hadoop Core (Support Ubuntu16, CentOS7)

## Requirements

Ansible 2.1

## Role Variables

|Variable|Default Value|Description|
|---|---|---|
```hadoop_user```|hduser|hadoop user account.
```java_home```|/usr/lib/jvm/java-8-openjdk-amd64|java home.
```hadoop_home```|/usr/local/hadoop|hadoop home.
```fs_defaultFS_address```|127.0.0.1|hdfs address.
```fs_defaultFS_port```|9000|hdfs port.
```dfs_secondary_http_address```|127.0.0.1|secondary namenode address.
```dfs_secondary_http_port```|50090|secondary namenode port.
```mapreduce_framework_name```|yarn|mapreduce framework name.
```yarn_resourcemanager_hostname```|127.0.0.1| yarn resourcemanager hostname.
```yarn_nodemanager_aux_services```|mapreduce_shuffle| yarn nodemanager aux services.
```hadoop_slaves```|['127.0.0.1']|hadoop slave address list.

## Example
```
### create a requirements.yml
- src: git+https://github.com/willyhutw/ansible-role-hadoop-core.git
  name: ansible-role-hadoop-core

### create a playbook.yml
- hosts: all
  become: yes
  roles:
    - roles/ansible-role-hadoop-core

### install this role
ansible-galaxy install -r requirements.yml -p ./roles

### run it!
ansible-playbook -i '192.168.33.151, 192.168.33.152, 192.168.33.153,' playbook.yml \
-e "ansible_ssh_user=vagrant ansible_ssh_pass=vagrant" \
-e "fs_defaultFS_address=192.168.33.151" \
-e "dfs_secondary_http_address=192.168.33.152" \
-e "yarn_resourcemanager_hostname=192.168.33.151" \
-e "{'hadoop_slaves':['192.168.33.152','192.168.33.153']}"
```

## License

MIT / BSD

## Author Information

willyhu.tw@gmail.com

